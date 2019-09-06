---
title: ' Componente de carga de imagen| Microsoft Docs'
description: Implementar componente de carga de imagen utilizando typescript
ms.custom: ''
manager: kvivek
ms.date: 04/23/2019
ms.service: powerapps
ms.topic: article
ms.author: nabuthuk
author: nkrb
---

# <a name="implementing-an-image-upload-component"></a>Implementar un componente de carga de imagen

[!INCLUDE[cc-beta-prerelease-disclaimer](../../../includes/cc-beta-prerelease-disclaimer.md)]

Este componente de ejemplo se representa como un botón `Upload` para cargar la imagen y una imagen predeterminada cuando se carga el componente por primera vez. Cuando hace clic en `Upload`, aparece un explorador de archivos para seleccionar una imagen.
 
La imagen seleccionada se genera en el componente. Mientras tanto, se muestra el botón `Remove` si es necesario reinicializar. Al hacer clic en el botón `Remove`, se muestra la imagen predeterminada.  

> [!div class="mx-imgBorder"]
> ![Componente de carga de imagen](../media/image-upload-control.png "Componente de carga de imagen")

## <a name="manifest"></a>Manifiesto

```xml
<?xml version="1.0" encoding="utf-8" ?>
<manifest>
  <control namespace="SampleNamespace" constructor="TSImageUploadControl" version="1.0.0" display-name-key="TS_ImageUploadControl_Display_Key" description-key="TSImageUploadControl_Desc_Key" control-type="standard">
    <property name="value" display-name-key="value_Display_Key" description-key="value_Desc_Key" of-type="Multiple" usage="bound" required="true" />
    <resources>
      <code path="index.ts" order="1" />
        <css path="css/TS_ImageUploadControl.css" order="1" />
      <img path="img/default.png" />
      <resx path="strings/TSImageUploadControl.1033.resx" version="1.0.0" />
    </resources>
    <feature-usage>
<uses-feature name="Device.pickFile" required="true" />
</feature-usage>
  </control>
</manifest>
```

## <a name="code"></a>Código

```TypeScript
import {IInputs, IOutputs} from "./generated/ManifestTypes";
'use strict';
// Define const here
// Default Image FileName
const DefaultImageFileName:string = "default.png";
// Show Error css classname
const ShowErrorClassName = "ShowError";
// No Image css classname
const NoImageClassName = "NoImage";
// 'RemoveButton' css class name
const RemoveButtonClassName = "RemoveButton";
export class TSImageUploadControl implements ComponentFramework.StandardControl<IInputs, IOutputs> 
{
// Value of the field is stored and used inside the control 
private _value: string | null;
// PowerApps component framework framework context, "Input Properties" containing the parameters, control metadata and interface functions.
private _context: ComponentFramework.Context<IInputs>;
// PowerApps component framework framework delegate which will be assigned to this object which would be called whenever an update happens. 
private _notifyOutputChanged: () => void;
// Control's container
private controlContainer: HTMLDivElement;
// button element created as part of this control
private uploadButton: HTMLButtonElement;
// button element created as part of this control
private removeButton: HTMLButtonElement;
// label element created as part of this control
private imgElement: HTMLImageElement;
// label element created as part of this control
private errorLabelElement: HTMLLabelElement;
/**
 * Empty constructor.
 */
constructor()
{
}
/**
 * Used to initialize the control instance. Controls can kick off remote server calls and other initialization actions here.
 * Data-set values are not initialized here, use updateView.
 * @param context The entire property bag available to control via Context Object; It contains values as set up by the customizer mapped to property names defined in the manifest, as well as utility functions.
 * @param notifyOutputChanged A callback method to alert the framework that the control has new outputs ready to be retrieved asynchronously.
 * @param state A piece of data that persists in one session for a single user. Can be set at any point in a controls life cycle by calling 'setControlState' in the Mode interface.
 * @param container If control is marked control-type='standard', it receives an empty div element within which it can render its content.
 */
public init(context: ComponentFramework.Context<IInputs>, notifyOutputChanged: () => void, state: ComponentFramework.Dictionary, container:HTMLDivElement)
{
    this._context = context;
    this._notifyOutputChanged = notifyOutputChanged;
    this.controlContainer = document.createElement("div");
    //Create an upload button to upload the image
    this.uploadButton = document.createElement("button");
    // Get the localized string from localized string 
    this.uploadButton.innerHTML = context.resources.getString("PCF_ImageUploadControl_Upload_ButtonLabel");
    this.uploadButton.addEventListener("click", this.onUploadButtonClick.bind(this));
    // Creating the label for the control and setting the relevant values.
    this.imgElement = document.createElement("img");
    //Create a remove button to reset the image
    this.removeButton = document.createElement("button");
    this.removeButton.classList.add(RemoveButtonClassName);
    // Get the localized string from localized string 
    this.removeButton.innerHTML = context.resources.getString("PCF_ImageUploadControl_Remove_ButtonLabel");
    this.removeButton.addEventListener("click", this.onRemoveButtonClick.bind(this));
    // Create an error label element
    this.errorLabelElement = document.createElement("label");
    // If there is a raw value bound means there already have an image
    if(this._context.parameters.value.raw)
    {
        this.imgElement.src = context.parameters.value.raw;
    }
    else
    {
        this.setDefaultImage();
    }
    // Adding the label and button created to the container DIV.
    this.controlContainer.appendChild(this.uploadButton);
    this.controlContainer.appendChild(this.imgElement);
    this.controlContainer.appendChild(this.removeButton);
    this.controlContainer.appendChild(this.errorLabelElement);
    container.appendChild(this.controlContainer);
}
/**
 * Called when any value in the property bag has changed. This includes field values, data-sets, global values such as container height and width, offline status, control metadata values such as label, visible, etc.
 * @param context The entire property bag available to control via Context Object; It contains values as set up by the customizer mapped to names defined in the manifest, as well as utility functions
 */
public updateView(context: ComponentFramework.Context<IInputs>): void
{
    // Always need to update the _context obj
    this._context = context;
}
/**
 * Button Event handler for the button created as part of this control
 * @param event
 */
private onUploadButtonClick(event: Event): void 
{   
    // context.device.pickFile(successCallback, errorCallback) is used to initiate the File Explorer
    // successCallback will be triggered if there successfully pick a file
    // errorCallback will be triggered if there is an error
    this._context.device.pickFile().then(this.processFile.bind(this), this.showError.bind(this));
}
/**
 * Button Event handler for the button created as part of this control
 * @param event
 */
private onRemoveButtonClick(event: Event): void 
{
    this.setDefaultImage();
}
/**
 * 
 * @param files 
 */
private processFile(files: ComponentFramework.FileObject[]): void
{
    if(files.length > 0)
    {
        let file: ComponentFramework.FileObject = files[0];
        try
        {
            let fileExtension :string|undefined;
            if(file && file.fileName)
            {
                fileExtension = file.fileName.split('.').pop();
            }
            if(fileExtension)
            {
                this.setImage(true, fileExtension, file.fileContent);
                this.controlContainer.classList.remove(NoImageClassName);
            }
            else
            {
                this.showError();
            }
        }
        catch(err)
        {
            this.showError();
        }
    }
}
/**
 * Set Default Image
 */
private setDefaultImage():void
{
    this._context.resources.getResource(DefaultImageFileName, this.setImage.bind(this, false, "png"), this.showError.bind(this));
    this.controlContainer.classList.add(NoImageClassName);
    // If it already has value, we need to update the output
    if(this._context.parameters.value.raw)
    {
        this._value = null;
        this._notifyOutputChanged();
    }
}
/**
 * Set the Image content
 * @param shouldUpdateOutput indicate if needs to inform the infra of the change
 * @param fileType file extension name like "png", "gif", "jpg"
 * @param fileContent file content, base64 format
 */
private setImage(shouldUpdateOutput:boolean, fileType: string, fileContent: string): void
{
    let imageUrl:string = this.generateImageSrcUrl(fileType, fileContent);
    this.imgElement.src = imageUrl;
    if(shouldUpdateOutput)
    {
        this.controlContainer.classList.remove(ShowErrorClassName);
        this._value = imageUrl;
        this._notifyOutputChanged();
    }
}
/**
 * Generate Image Element src url
 * @param fileType file extension
 * @param fileContent file content, base 64 format
 */
private generateImageSrcUrl(fileType: string, fileContent: string): string
{
    return  "data:image/" + fileType + ";base64, " + fileContent;
}
/** 
 *  Show Error Message
 */
private showError(): void
{
    this.errorLabelElement.innerText = this._context.resources.getString("PCF_ImageUploadControl_Can_Not_Find_File");
    this.controlContainer.classList.add(ShowErrorClassName);
}
/** 
 * It is called by the framework prior to a control receiving new data. 
 * @returns an object based on nomenclature defined in manifest, expecting object[s] for property marked as “bound” or “output”
 */
public getOutputs(): IOutputs
{
    // return outputs
    let result: IOutputs = 
        {
            value: this._value!
        };
        return result;
}
/** 
 * Called when the control is to be removed from the DOM tree. Controls should use this call for cleanup.
 * i.e. canceling any pending remote calls, removing listeners, etc.
 */
public destroy(): void
{
}
}
```

## <a name="resources"></a>Recursos

```css
.SampleNamespace\.TSImageUploadControl button{
text-decoration: none;
display: block;
font-size: 14px;
margin: 4px 6px;
cursor: pointer;
color: white;
border-radius: 0px;
background-color: rgb(59, 121, 183);
border: none;
padding: 5px;
text-align: center;
}
.SampleNamespace\.TSImageUploadControl img{
display: block;
box-shadow: 0 5px 10px 0 rgba(30, 30, 30, 0.3);
width: 100px;
height: 100px;
}
.SampleNamespace\.TSImageUploadControl .NoImage>.RemoveButton {
display: none;
}
.SampleNamespace\.TSImageUploadControl label{
display: none;
}
.SampleNamespace\.TSImageUploadControl .ShowError>label{
display: block;
color: red;
}
```

```XML
<?xml version="1.0" encoding="utf-8"?>
<root>
<xsd:schema id="root" xmlns="" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">
<xsd:import namespace="http://www.w3.org/XML/1998/namespace" />
<xsd:element name="root" msdata:IsDataSet="true">
  <xsd:complexType>
    <xsd:choice maxOccurs="unbounded">
      <xsd:element name="metadata">
        <xsd:complexType>
          <xsd:sequence>
            <xsd:element name="value" type="xsd:string" minOccurs="0" />
          </xsd:sequence>
          <xsd:attribute name="name" use="required" type="xsd:string" />
          <xsd:attribute name="type" type="xsd:string" />
          <xsd:attribute name="mimetype" type="xsd:string" />
          <xsd:attribute ref="xml:space" />
        </xsd:complexType>
      </xsd:element>
      <xsd:element name="assembly">
        <xsd:complexType>
          <xsd:attribute name="alias" type="xsd:string" />
          <xsd:attribute name="name" type="xsd:string" />
        </xsd:complexType>
      </xsd:element>
      <xsd:element name="data">
        <xsd:complexType>
          <xsd:sequence>
            <xsd:element name="value" type="xsd:string" minOccurs="0" msdata:Ordinal="1" />
            <xsd:element name="comment" type="xsd:string" minOccurs="0" msdata:Ordinal="2" />
          </xsd:sequence>
          <xsd:attribute name="name" type="xsd:string" use="required" msdata:Ordinal="1" />
          <xsd:attribute name="type" type="xsd:string" msdata:Ordinal="3" />
          <xsd:attribute name="mimetype" type="xsd:string" msdata:Ordinal="4" />
          <xsd:attribute ref="xml:space" />
        </xsd:complexType>
      </xsd:element>
      <xsd:element name="resheader">
        <xsd:complexType>
          <xsd:sequence>
            <xsd:element name="value" type="xsd:string" minOccurs="0" msdata:Ordinal="1" />
          </xsd:sequence>
          <xsd:attribute name="name" type="xsd:string" use="required" />
        </xsd:complexType>
      </xsd:element>
    </xsd:choice>
  </xsd:complexType>
</xsd:element>
</xsd:schema>
<resheader name="resmimetype">
<value>text/microsoft-resx</value>
</resheader>
<resheader name="version">
<value>2.0</value>
</resheader>
<resheader name="reader">
<value>System.Resources.ResXResourceReader, System.Windows.Forms, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089</value>
</resheader>
<resheader name="writer">
<value>System.Resources.ResXResourceWriter, System.Windows.Forms, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089</value>
</resheader>
<data name="PCF_ImageUploadControl_Upload_ButtonLabel" xml:space="preserve">
<value>Upload</value>
<comment>Label for ImageUploadControl's Upload Button</comment>
</data>
<data name="PCF_ImageUploadControl_Remove_ButtonLabel" xml:space="preserve">
<value>Remove</value>
<comment>Label for ImageUploadControl's Remove Button</comment>
</data>
<data name="PCF_ImageUploadControl_Can_Not_Find_File" xml:space="preserve">
<value>Image not found</value>
<comment>Error String Can Not Find File</comment>
</data>
</root>
```

Este ejemplo muestra cómo crear un selector de imagen y muestra la API de dispositivo y la API de recursos para cargar la imagen definida en manifiesto.El contenido de la imagen se almacena en codificación base64 y se puede guardar y recuperar.  

El método `resources.getResource` toma la entrada como el nombre de recurso web definido en el manifiesto del componente y carga ese recurso web. El componente genera un botón `Upload` y la imagen predeterminada para la representación inicial. Las imágenes se definen en el nodo [recurso](../reference/resources.md) del manifiesto.  

```xml
    <resources>
      <code path="index.ts" order="1" />
        <css path="css/TS_ImageUploadControl.css" order="1" />
      <img path="img/default.png" />
      <resx path="strings/TSImageUploadControl.1033.resx" version="1.0.0" />
    </resources> 
 ```
 
La `successCallback` se desencadenará y el contenido del recurso se inserta en la `successCallback`. A continuación use el 'src' del elemento de imagen para apuntar al contenido y se carga la imagen predeterminada.
 
El método `device.pickFile` abre un cuadro de diálogo para seleccionar archivos de su equipo (cliente web) o dispositivo móvil (clientes móviles). Para el escritorio, abre el explorador de archivos, para el cliente móvil, abre la biblioteca de la foto. Al hacer clic en el botón  `upload`, se desencadena el  `pickFile` de la API de dispositivo y el usuario selecciona el archivo. Una vez seleccionado el archivo correctamente, el nombre del archivo, el contenido del archivo se insertará en la `successCallback`. 

> [!NOTE]
> Si el mismo formulario o entidad se usa en el antiguo cliente web, el campo mostrará el componente de texto predefinido en el antiguo cliente web, donde puede haber problemas de UX.  Para hacer que esté oculto en el antiguo cliente web, podríamos desactivar la casilla **Visibilidad** y activar la casilla **Ocultar control predeterminado** a la vez. 

### <a name="related-topics"></a>Temas relacionados

[Descargar componentes de ejemplo](https://go.microsoft.com/fwlink/?linkid=2088525)<br/>
[Referencia de la API de marco de componentes de PowerApps](../reference/index.md)<br/>
[Referencia de esquema de manifiesto del marco de componentes de PowerApps](../manifest-schema-reference/index.md)