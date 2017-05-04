---
title: "Манифесты приложений для решений Office | Microsoft Docs"
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
  - "манифесты приложения [разработка решений Office в Visual Studio]"
ms.assetid: dd38685f-f429-4a35-8c11-a03372c9770a
caps.latest.revision: 41
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 40
---
# Манифесты приложений для решений Office
  Манифест приложения представляет собой XML\-файл с описанием сборок, загружаемых в решении Microsoft Office. Средства разработки для Microsoft Office в Visual Studio используют схему манифестов приложений [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)], определенную в справочнике [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md).  
  
 Манифесты приложений для решений Office используют перечисленные ниже элементы и атрибуты [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)].  
  
|Элемент|Описание|Атрибуты|  
|-------------|--------------|--------------|  
|[Элемент &#60;assembly&#62; &#40;приложение ClickOnce&#41;](../Topic/%3Cassembly%3E%20Element%20(ClickOnce%20Application).md)|Обязательный. Это элемент верхнего уровня.|`manifestVersion`|  
|[Элемент &#60;assemblyIdentity&#62; &#40;приложение ClickOnce&#41;](../Topic/%3CassemblyIdentity%3E%20Element%20(ClickOnce%20Application).md)|Обязательный. Определяет основную сборку приложения [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)].|`name`<br /><br /> `version`<br /><br /> `publicKeyToken`<br /><br /> `processorArchitecture`<br /><br /> `language`|  
|[Элемент &#60;trustInfo&#62; &#40;приложение ClickOnce&#41;](../Topic/%3CtrustInfo%3E%20Element%20(ClickOnce%20Application).md)|Определяет требования к безопасности приложения.|Нет|  
|[Элемент &#60;entryPoint&#62; &#40;приложение ClickOnce&#41;](../Topic/%3CentryPoint%3E%20Element%20(ClickOnce%20Application).md)|Обязательный. Определяет точку входа в код приложения для выполнения.|`name`<br /><br /> `dependencyName`<br /><br /> `customHostSpecified`|  
|[Элемент &#60;dependency&#62; &#40;приложение ClickOnce&#41;](../Topic/%3Cdependency%3E%20Element%20(ClickOnce%20Application).md)|Обязательный. Определяет все зависимости, необходимые для выполнения приложения. При необходимости определяет сборки, которые требуется установить предварительно.|Нет|  
|[Элемент &#60;file&#62; &#40;приложение ClickOnce&#41;](../Topic/%3Cfile%3E%20Element%20(ClickOnce%20Application).md)|Обязательный. Определяет все не являющиеся сборками файлы, используемые приложением. Может включать данные изоляции модели COM, связанные с этим файлом.|`name`<br /><br /> `size`|  
  
 Манифесты приложений для решений Office имеют указанный ниже элемент в пространстве имен `co.v1`.  
  
```  
<entryPoint> <co.v1:customHostSpecified /> </entryPoint>   
```  
  
 Эти манифесты приложений также имеют в пространстве имен `vstav3` указанные ниже элементы и атрибуты.  
  
```  
<addIn> <entryPointsCollection> <entryPoints> <entryPoint> </entryPoint> </entryPoints> </entryPointsCollection> <update></update> <postActions> <postAction> <postActionData> </postActionData> <postAction> </postActions> <application> <customizations> <customization> </customization> </customizations> </application </addIn>  
```  
  
|Элемент|Описание|Атрибуты|  
|-------------|--------------|--------------|  
|[элемент &#60;customHostSpecified&#62; &#40;разработка решений Office в Visual Studio&#41;](../vsto/customhostspecified-element-office-development-in-visual-studio.md)|Обязательный. Помечает манифест как решение Office.|Нет|  
|[элемент &#60;addin&#62; &#40;разработка решений Office в Visual Studio&#41;](../vsto/addin-element-office-development-in-visual-studio.md)|Обязательный. Сохраняет точки входа в одном пространстве имен.|Нет|  
|[Элемент &#60;entryPointsCollection&#62; &#40;разработка решений Office в Visual Studio&#41;](../vsto/entrypointscollection-element-office-development-in-visual-studio.md)|Обязательный. Группирует все сборки для одного или нескольких решений Office.|`id`|  
|[элемент &#60;entryPoints&#62; &#40;разработка решений Office в Visual Studio&#41;](../vsto/entrypoints-element-office-development-in-visual-studio.md)|Обязательный. Группирует все сборки для запуска решения Office.|Нет|  
|[элемент &#60;entryPoint&#62; &#40;разработка решений Office в Visual Studio&#41;](../vsto/entrypoint-element-office-development-in-visual-studio.md)|Обязательный. Указывает сборку, запускаемую в решении Office.|`class`<br /><br /> `contract`|  
|[элемент &#60;update&#62; &#40;разработка решений Office в Visual Studio&#41;](../vsto/update-element-office-development-in-visual-studio.md)|Обязательный. Настраивает обновления для решения.|`enabled`<br /><br /> `expiration`|  
|[элемент &#60;postActions&#62; &#40;разработка решений Office в Visual Studio&#41;](../vsto/postactions-element-office-development-in-visual-studio.md)|Необязательный. Группирует все действия, выполняемые после развертывания, которые запускаются после установки решений Office.|Нет|  
|[элемент &#60;postAction&#62; &#40;разработка решений Office в Visual Studio&#41;](../vsto/postaction-element-office-development-in-visual-studio.md)|Необязательный. Указывает действие, выполняемое после развертывания.|Нет|  
|[Элемент &#60;postActionData&#62; &#40;разработка решений Office в Visual Studio&#41;](../vsto/postactiondata-element-office-development-in-visual-studio.md)|Необязательный. Настраивает данные для действия, выполняемого после развертывания.|Нет|  
|[элемент &#60;application&#62; &#40;разработка решений Office в Visual Studio&#41;](../vsto/application-element-office-development-in-visual-studio.md)|Обязательный. Инкапсулирует сведения о приложении в один узел.|Нет|  
|[Элемент &#60;customizations&#62; &#40;разработка решений Office в Visual Studio&#41;](../vsto/customizations-element-office-development-in-visual-studio.md)|Обязательный. Сохраняет все сведения о ведущем приложении в отдельном пространстве имен.|Нет|  
|[элемент &#60;customization&#62; &#40;разработка решений Office в Visual Studio&#41;](../vsto/customization-element-office-development-in-visual-studio.md)|Обязательный. Сохраняет сведения о ведущем приложении в отдельном пространстве имен.|`xmlns`|  
|[элемент &#60;document&#62; &#40;разработка решений Office в Visual Studio&#41;](../vsto/document-element-office-development-in-visual-studio.md)|Является обязательным только для решений на уровне документа. Хранит сведения о настройках.|`solutionId`|  
|[элемент &#60;appAddin&#62; &#40;разработка решений Office в Visual Studio&#41;](../vsto/appaddin-element-office-development-in-visual-studio.md)|Является обязательным только для решений на уровне приложения. Хранит сведения о настройках.|`application`<br /><br /> `loadBehavior`<br /><br /> `keyName`|  
|[Элемент &#60;friendlyName&#62; &#40;разработка решений Office в Visual Studio&#41;](../vsto/friendlyname-element-office-development-in-visual-studio.md)|Необязательный. Хранит имя надстройки VSTO, которое будет отображаться в списке установленных надстроек VSTO.|Нет|  
|[элемент &#60;description&#62; &#40;разработка решений Office в Visual Studio&#41;](../vsto/description-element-office-development-in-visual-studio.md)|Является обязательным только для надстроек VSTO. Хранит описание, которое будет отображаться в списке установленных программ.|Нет|  
|[элемент &#60;formRegions&#62; &#40;разработка решений Office в Visual Studio&#41;](../vsto/formregions-element-office-development-in-visual-studio.md)|Является обязательным только для надстроек VSTO для Outlook, включающих области форм.|Нет|  
|[Элемент &#60;formRegion&#62; &#40;разработка решений Office в Visual Studio&#41;](../vsto/formregion-element-office-development-in-visual-studio.md)|Является обязательным только для надстроек VSTO для Outlook, включающих области форм.|`Name`|  
|[Элемент &#60;vstoRuntime&#62; &#40;разработка решений Office в Visual Studio&#41;](../vsto/vstoruntime-element-office-development-in-visual-studio.md)|Обязательный. Указывает конкретную версию среды выполнения средств Visual Studio для Office, поддерживаемую решением Office.|`release`<br /><br /> `version`<br /><br /> `supportUrl`|  
  
## Заметки  
 Манифесты приложений и развертывания в решениях Office можно менять вручную. После этого манифесты приложений и развертывания необходимо подписать повторно с помощью Инструмента создания и изменения манифестов \(mage.exe и mageui.exe\). Для получения дополнительной информации см. [Практическое руководство. Повторное подписание манифестов приложения и развертывания](../Topic/How%20to:%20Re-sign%20Application%20and%20Deployment%20Manifests.md).  
  
## Расположение файлов  
 Манифест приложения определяется для отдельной версии решения. По этой причине манифест приложения следует хранить отдельно от манифеста развертывания.[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] помещает файлы, относящиеся к конкретной версии, в подкаталог, название которого соответствует версии и который находится в подкаталоге **Файлы приложения** каталога публикации.  
  
## Синтаксис имени файла  
 Имя файла манифеста приложения должно содержать полное имя и расширение приложения, определенные в элементе `assemblyIdentity`, и иметь расширение MANIFEST. Например, манифест приложения, ссылающийся на настройки OutlookAddIn1.dll, будет иметь следующий синтаксис имени файла:  
  
 `OutlookAddIn1.dll.manifest`  
  
## См. также  
 [Манифесты развертывания для решений Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md)  
  
  