---
title: "элемент &lt;addin&gt; (разработка решений Office в Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "манифесты приложения [разработка решений Office в Visual Studio], элемент <addin>"
  - "addin - элемент"
  - "элемент <addin>"
ms.assetid: 4abec4c3-8c7c-4b2b-9128-79fa4e863281
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# элемент &lt;addin&gt; (разработка решений Office в Visual Studio)
  Элемент `addin` пространства имен `vstav3`  содержит сведения, относящиеся к настройкам уровня документа и надстройкам VSTO Microsoft Office, разработанным с помощью Visual Studio.  
  
## Синтаксис  
  
```  
<addIn>  
  <entryPointsCollection>  
    <entryPoints>  
      <entryPoint>  
      </entryPoint>  
    </entryPoints>  
  </entryPointsCollection>  
  <update></update>  
  <postActions>  
    <postAction>  
      <postActionData>  
      </postActionData>  
    <postAction>  
  </postActions>  
  <application>  
    <customization>  
    </customization>  
  </application  
</addIn>  
```  
  
## Элементы и атрибуты  
 Элемент `addin` пространства имен `vstav3`  содержит сведения о решений Office и приложении Microsoft Office. Этот элемент должен принадлежать следующему пространству имен: `vstav3=urn:schemas-microsoft-com:vsta.v3`. Дочерние элементы также должны быть в этом пространство имен.  
  
 У элемента `addin` нет атрибутов.  
  
 Элемент `addin` имеет указанные ниже дочерние элементы.  
  
### entryPoints  
 Обязательный. Элемент `entryPoints` описывается в разделе [элемент &#60;entryPoints&#62; &#40;разработка решений Office в Visual Studio&#41;](../vsto/entrypoints-element-office-development-in-visual-studio.md).  
  
### обновить  
 Обязательный. Элемент `update` описывается в разделе [элемент &#60;update&#62; &#40;разработка решений Office в Visual Studio&#41;](../vsto/update-element-office-development-in-visual-studio.md).  
  
### postActions  
 Необязательный. Элемент `postActions` описывается в разделе [элемент &#60;postActions&#62; &#40;разработка решений Office в Visual Studio&#41;](../vsto/postactions-element-office-development-in-visual-studio.md).  
  
### приложение  
 Обязательный. Элемент `application` описывается в разделе [элемент &#60;application&#62; &#40;разработка решений Office в Visual Studio&#41;](../vsto/application-element-office-development-in-visual-studio.md).  
  
## Пример настройки на уровне документа  
  
### Описание  
 В следующем примере кода показан элемент `addin` в решении Office уровня документа, которое развернуто с помощью [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Этот пример кода является частью большего примера, приведенного в разделе [Манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md).  
  
### Код  
  
```  
<vstav3:addIn xmlns:vstav3="urn:schemas-microsoft-com:vsta.v3"> <vstav3:entryPointsCollection> <vstav3:entryPoints> <vstav3:entryPoint class="ContosoExcelWorkbook.ThisWorkbook"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> <vstav3:entryPoint class="ContosoExcelWorkbook.Sheet1"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> <vstav3:entryPoint class="ContosoExcelWorkbook.Sheet2"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> <vstav3:entryPoint class="ContosoExcelWorkbook.Sheet3"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> </vstav3:entryPoints> </vstav3:entryPointsCollection> <vstav3:update enabled="true"> <vstav3:expiration maximumAge="7" unit="days" /> </vstav3:update> <vstav3:application> <vstov4:customizations xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4"> <vstov4:customization> <vstov4:document solutionId="73e" /> </vstov4:customization> </vstov4:customizations> </vstav3:application> </vstav3:addIn>  
```  
  
## Примеры надстройки VSTO  
  
### Описание  
 В следующем примере кода показан элемент `addin` в решении Office уровня приложения, которое развернуто с помощью [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Этот пример кода является частью большего примера, приведенного в разделе [Манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md).  
  
### Код  
  
```  
<vstav3:addIn xmlns:vstav3="urn:schemas-microsoft-com:vsta.v3"> <vstav3:entryPointsCollection> <vstav3:entryPoints> <vstav3:entryPoint class="ContosoOutlookAddIn.ThisAddIn"> <assemblyIdentity name="ContosoOutlookAddIn" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> </vstav3:entryPoints> </vstav3:entryPointsCollection> <vstav3:update enabled="true"> <vstav3:expiration maximumAge="7" unit="days" /> </vstav3:update> <vstav3:application> <vstov4:customizations xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4"> <vstov4:customization> <vstov4:appAddIn application="Outlook" loadBehavior="3" keyName="ContosoOutlookAddIn"> <vstov4:friendlyName> ContosoOutlookAddIn </vstov4:friendlyName> <vstov4:description> ContosoOutlookAddIn - Outlook VSTO Add-in created with Visual Studio Tools for Office </vstov4:description> <vstov4:formRegions> <vstov4:formRegion name="OutlookAddIn1.FormRegion1"> <vstov4:messageClass name="IPM.Note" /> <vstov4:messageClass name="IPM.Contact" /> <vstov4:messageClass name="IPM.Appointment" /> </vstov4:formRegion> </vstov4:formRegions> </vstov4:appAddIn> </vstov4:customization> </vstov4:customizations> </vstav3:application> </vstav3:addIn>  
```  
  
## См. также  
 [Манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md)   
 [Манифесты развертывания для решений Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md)  
  
  