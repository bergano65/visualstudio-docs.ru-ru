---
title: Манифесты приложений для решений Office | Документы Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0fa1ee09b3218fbcb485d7c3cd23e23ec18f463c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="application-manifests-for-office-solutions"></a>Манифесты приложений для решений Office
  Манифест приложения представляет собой XML-файл с описанием сборок, загружаемых в решении Microsoft Office. Средства разработки для Microsoft Office в Visual Studio используют схему манифестов приложений [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] , определенную в справочнике [ClickOnce Application Manifest](/visualstudio/deployment/clickonce-application-manifest) .  
  
 Манифесты приложений для решений Office используют перечисленные ниже элементы и атрибуты [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] .  
  
|Элемент|Описание|Атрибуты|  
|-------------|-----------------|----------------|  
|[&#60;сборка&#62; элемент &#40;приложения ClickOnce&#41;](/visualstudio/deployment/assembly-element-clickonce-deployment)|Обязательно. Это элемент верхнего уровня.|`manifestVersion`|  
|[&#60;assemblyIdentity&#62; элемент &#40;приложения ClickOnce&#41;](/visualstudio/deployment/assemblyidentity-element-clickonce-deployment)|Обязательно. Определяет основную сборку приложения [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] .|`name`<br /><br /> `version`<br /><br /> `publicKeyToken`<br /><br /> `processorArchitecture`<br /><br /> `language`|  
|[&#60;trustInfo&#62; элемент &#40;приложения ClickOnce&#41;](/visualstudio/deployment/trustinfo-element-clickonce-application)|Определяет требования к безопасности приложения.|Нет|  
|[&#60;entryPoint&#62; элемент &#40;приложения ClickOnce&#41;](/visualstudio/deployment/entrypoint-element-clickonce-application)|Обязательно. Определяет точку входа в код приложения для выполнения.|`name`<br /><br /> `dependencyName`<br /><br /> `customHostSpecified`|  
|[&#60;зависимости&#62; элемент &#40;приложения ClickOnce&#41;](/visualstudio/deployment/dependency-element-clickonce-deployment)|Обязательно. Определяет все зависимости, необходимые для выполнения приложения. При необходимости определяет сборки, которые требуется установить предварительно.|Нет|  
|[&#60;файл&#62; элемент &#40;приложения ClickOnce&#41;](/visualstudio/deployment/file-element-clickonce-application)|Обязательно. Определяет все не являющиеся сборками файлы, используемые приложением. Может включать данные изоляции модели COM, связанные с этим файлом.|`name`<br /><br /> `size`|  
  
 Манифесты приложений для решений Office имеют указанный ниже элемент в пространстве имен `co.v1` .  
  
```  
<entryPoint>  
    <co.v1:customHostSpecified />  
</entryPoint>   
```  
  
 Эти манифесты приложений также имеют в пространстве имен `vstav3` указанные ниже элементы и атрибуты.  
  
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
    <customizations>  
      <customization>  
      </customization>  
    </customizations>  
  </application  
</addIn>  
```  
  
|Элемент|Описание|Атрибуты|  
|-------------|-----------------|----------------|  
|[&#60;customHostSpecified&#62; элемент &#40;разработка решений Office в Visual Studio&#41;](../vsto/customhostspecified-element-office-development-in-visual-studio.md)|Обязательно. Помечает манифест как решение Office.|Нет|  
|[&#60;Надстройка&#62; элемент &#40;разработка решений Office в Visual Studio&#41;](../vsto/addin-element-office-development-in-visual-studio.md)|Обязательно. Сохраняет точки входа в одном пространстве имен.|Нет|  
|[&#60;entryPointsCollection&#62; элемент &#40;разработка решений Office в Visual Studio&#41;](../vsto/entrypointscollection-element-office-development-in-visual-studio.md)|Обязательно. Группирует все сборки для одного или нескольких решений Office.|`id`|  
|[&#60;entryPoints&#62; элемент &#40;разработка решений Office в Visual Studio&#41;](../vsto/entrypoints-element-office-development-in-visual-studio.md)|Обязательно. Группирует все сборки для запуска решения Office.|Нет|  
|[&#60;entryPoint&#62; элемент &#40;разработка решений Office в Visual Studio&#41;](../vsto/entrypoint-element-office-development-in-visual-studio.md)|Обязательно. Указывает сборку, запускаемую в решении Office.|`class`<br /><br /> `contract`|  
|[&#60;обновление&#62; элемент &#40;разработка решений Office в Visual Studio&#41;](../vsto/update-element-office-development-in-visual-studio.md)|Обязательно. Настраивает обновления для решения.|`enabled`<br /><br /> `expiration`|  
|[&#60;postActions&#62; элемент &#40;разработка решений Office в Visual Studio&#41;](../vsto/postactions-element-office-development-in-visual-studio.md)|Необязательный. Группирует все действия, выполняемые после развертывания, которые запускаются после установки решений Office.|Нет|  
|[&#60;postAction&#62; элемент &#40;разработка решений Office в Visual Studio&#41;](../vsto/postaction-element-office-development-in-visual-studio.md)|Необязательный. Указывает действие, выполняемое после развертывания.|Нет|  
|[&#60;postActionData&#62; элемент &#40;разработка решений Office в Visual Studio&#41;](../vsto/postactiondata-element-office-development-in-visual-studio.md)|Необязательный. Настраивает данные для действия, выполняемого после развертывания.|Нет|  
|[&#60;приложение&#62; элемент &#40;разработка решений Office в Visual Studio&#41;](../vsto/application-element-office-development-in-visual-studio.md)|Обязательно. Инкапсулирует сведения о приложении в один узел.|Нет|  
|[&#60;настройки&#62; элемент &#40;разработка решений Office в Visual Studio&#41;](../vsto/customizations-element-office-development-in-visual-studio.md)|Обязательно. Сохраняет все сведения о ведущем приложении в отдельном пространстве имен.|Нет|  
|[&#60;Настройка&#62; элемент &#40;разработка решений Office в Visual Studio&#41;](../vsto/customization-element-office-development-in-visual-studio.md)|Обязательно. Сохраняет сведения о ведущем приложении в отдельном пространстве имен.|`xmlns`|  
|[&#60;документ&#62; элемент &#40;разработка решений Office в Visual Studio&#41;](../vsto/document-element-office-development-in-visual-studio.md)|Является обязательным только для решений на уровне документа. Хранит сведения о настройках.|`solutionId`|  
|[&#60;appAddin&#62; элемент &#40;разработка решений Office в Visual Studio&#41;](../vsto/appaddin-element-office-development-in-visual-studio.md)|Является обязательным только для решений на уровне приложения. Хранит сведения о настройках.|`application`<br /><br /> `loadBehavior`<br /><br /> `keyName`|  
|[&#60;friendlyName&#62; элемент &#40;разработка решений Office в Visual Studio&#41;](../vsto/friendlyname-element-office-development-in-visual-studio.md)|Необязательный. Хранит имя надстройки VSTO, которое будет отображаться в списке установленных надстроек VSTO.|Нет|  
|[&#60;Описание&#62; элемент &#40;разработка решений Office в Visual Studio&#41;](../vsto/description-element-office-development-in-visual-studio.md)|Является обязательным только для надстроек VSTO. Хранит описание, которое будет отображаться в списке установленных программ.|Нет|  
|[&#60;formRegions&#62; элемент &#40;разработка решений Office в Visual Studio&#41;](../vsto/formregions-element-office-development-in-visual-studio.md)|Является обязательным только для надстроек VSTO для Outlook, включающих области форм.|Нет|  
|[&#60;formRegion&#62; элемент &#40;разработка решений Office в Visual Studio&#41;](../vsto/formregion-element-office-development-in-visual-studio.md)|Является обязательным только для надстроек VSTO для Outlook, включающих области форм.|`Name`|  
|[&#60;vstoRuntime&#62; элемент &#40;разработка решений Office в Visual Studio&#41;](../vsto/vstoruntime-element-office-development-in-visual-studio.md)|Обязательно. Указывает конкретную версию среды выполнения средств Visual Studio для Office, поддерживаемую решением Office.|`release`<br /><br /> `version`<br /><br /> `supportUrl`|  
  
## <a name="remarks"></a>Примечания  
 Манифесты приложений и развертывания в решениях Office можно менять вручную. После этого манифесты приложений и развертывания необходимо подписать повторно с помощью Инструмента создания и изменения манифестов (mage.exe и mageui.exe). Для получения дополнительной информации см. [How to: Re-sign Application and Deployment Manifests](/visualstudio/deployment/how-to-re-sign-application-and-deployment-manifests).  
  
## <a name="file-location"></a>Расположение файлов  
 Манифест приложения определяется для отдельной версии решения. По этой причине манифест приложения следует хранить отдельно от манифеста развертывания. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] помещает файлы, относящиеся к конкретной версии, в подкаталог, название которого соответствует версии и который находится в подкаталоге **Файлы приложения** каталога публикации.  
  
## <a name="file-name-syntax"></a>Синтаксис имени файла  
 Имя файла манифеста приложения должно содержать полное имя и расширение приложения, определенные в элементе `assemblyIdentity` , и иметь расширение MANIFEST. Например, манифест приложения, ссылающийся на настройки OutlookAddIn1.dll, будет иметь следующий синтаксис имени файла:  
  
 `OutlookAddIn1.dll.manifest`  
  
## <a name="see-also"></a>См. также  
 [Манифесты развертывания для решений Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Манифест приложения ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  