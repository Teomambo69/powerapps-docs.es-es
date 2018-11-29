---
title: Recursos web de hoja de estilos (XSL) (aplicaciones basadas en modelos) | Microsoft Docs
description: Obtenga más información sobre el uso de los recursos Web de hoja de estilo (XSL) para transformar datos XML.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: KumarVivek
ms.author: kvivek
manager: shilpas
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="stylesheet-xsl-web-resources"></a>Recursos web de hoja de estilo (XSL)

<!-- https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/stylesheet-xsl-web-resources -->


Use recursos web de hoja de estilo (XSL) para transformar los datos XML.  
  
## <a name="capabilities-of-xsl-web-resources"></a>Capacidades de los recursos web XSL  
 Use los recursos web XSL para transformar los datos XML usados por la solución.  
  
 Los recursos web siguientes trabajan juntos para representar una página que muestra una tabla con los datos del recurso web XML. Los archivos de origen de estos recursos web forman parte del ejemplo Importar recursos web que se incluye en la carpeta **filestoimport**. Descargar el ejemplo de [Importar archivos como recursos web](https://code.msdn.microsoft.com/Import-files-as-web-f84ad8dc).  
  
 **Recurso web HTML:** sample_/ImportWebResources/Content/ShowData.htm  
 ```html  
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">  
<html>  
<head>  
 <title></title>  
 <script src="Script/Script.js" type="text/javascript"></script>  
 <link href="CSS/Styles.css" rel="stylesheet" type="text/css" />  
</head>  
<body onload="SDK.ImportWebResources.showData()">  
 <div id="results" />  
</body>  
</html>  
```  
  
 **Recurso web XSL:** sample_/ImportWebResources/XSL/Transform.xslt  
 ```xml  
<?xml version="1.0" encoding="utf-8"?>  
<xsl:stylesheet version="1.0"  
                xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
                xmlns:msxsl="urn:schemas-microsoft-com:xslt"  
                exclude-result-prefixes="msxsl"  
>  
 <xsl:output method="xml"  
             indent="yes"/>  
  
 <xsl:template match="@* | node()">  
  <xsl:copy>  
   <xsl:apply-templates select="@* | node()"/>  
  </xsl:copy>  
 </xsl:template>  
  
 <xsl:template match="people">  
  <xsl:element name="table">  
   <xsl:element name="thead">  
    <xsl:element name="tr">  
     <xsl:element name="th">  
      <xsl:text>First Name</xsl:text>  
     </xsl:element>  
     <xsl:element name="th">  
      <xsl:text>Last Name</xsl:text>  
     </xsl:element>  
    </xsl:element>  
   </xsl:element>  
   <xsl:element name="tbody">  
    <xsl:apply-templates />  
   </xsl:element>  
  </xsl:element>  
  
 </xsl:template>  
  
 <xsl:template match="person">  
  <xsl:element name="tr">  
   <xsl:element name="td">  
    <xsl:value-of select="@firstName"/>  
   </xsl:element>  
   <xsl:element name="td">  
    <xsl:value-of select="@lastName"/>  
   </xsl:element>  
  </xsl:element>  
  
 </xsl:template>  
  
</xsl:stylesheet>  
  
```  
  
 **Recurso web XML:** sample_/ImportWebResources/Data/Data.xml  
 ```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<people>  
 <person firstName="Apurva"  
         lastName="Dalia" />  
 <person firstName="Ofer"  
         lastName="Daliot" />  
 <person firstName="Jim"  
         lastName="Daly" />  
 <person firstName="Ryan"  
         lastName="Danner" />  
 <person firstName="Mike"  
         lastName="Danseglio" />  
 <person firstName="Alex"  
         lastName="Darrow" />  
</people>  
```  
  
 **Recurso web de script:** sample_/ImportWebResources/Script/Script.js  
 ```javascript  
//If the SDK namespace object is not defined, create it.  
if (typeof (SDK) == "undefined")  
{ SDK = {}; }  
// Create Namespace container for functions in this library;  
SDK.ImportWebResources = {  
 dataFile: "Data/Data.xml",  
 transformFile: "XSL/Transform.xslt",  
 showData: function () {  
  
  //Create an XML document from the Data.xml file  
  var dataXml = new ActiveXObject("Msxml2.DOMDocument.6.0");  
  dataXml.async = false;  
  dataXml.load(this.dataFile);  
  
  //Create an XML document from the Transform.xslt file  
  var transformXSLT = new ActiveXObject("Msxml2.DOMDocument.6.0");  
  transformXSLT.async = false;  
  transformXSLT.load(this.transformFile);  
  
  // Set the innerHTML of the results area to the output of the transformation.  
  var resultsArea = document.getElementById("results");  
  resultsArea.innerHTML = dataXml.transformNode(transformXSLT);  
 }  
  
}  
```  
  
 **Recurso web CSS:** sample_/ImportWebResources/CSS/Styles.css  
 ```css
body  
{  
    font-family: Calibri;  
}  
table  
{  
    border: 1px solid gray;  
    border-collapse: collapse;  
}  
th  
{  
    text-align: left;  
    border: 1px solid gray;  
}  
td  
{  
    border: 1px solid gray;  
}  
```  
  
### <a name="see-also"></a>Vea también  
 [Recursos web](web-resources.md)   
 [Uso de recursos web de página web (HTML)](webpage-html-web-resources.md)   
 [Uso de recursos web de hojas de estilo (CSS)](css-web-resources.md)   
 [Usar recursos web de script (JScript)](script-jscript-web-resources.md)   
 [Uso de recursos web de datos (XML)](data-xml-web-resources.md)   
 [Uso de recursos web de imagen (JPG, PNG, GIF)](image-web-resources.md)   
