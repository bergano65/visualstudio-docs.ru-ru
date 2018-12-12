---
title: Манифесты приложений для решений Office
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9665be31a59de33713f981889bc8cb8a8cb55eea
ms.sourcegitcommit: 20c0991d737c540750c613c380cd4cf5bb07de51
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2018
ms.locfileid: "53248180"
---
# <a name="application-manifests-for-office-solutions"></a>Манифесты приложений для решений Office
  Манифест приложения представляет собой XML-файл с описанием сборок, загружаемых в решении Microsoft Office. Средства разработки Microsoft Office в Visual Studio используют [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] схему манифестов приложений, определенных в [манифест приложения ClickOnce](/visualstudio/deployment/clickonce-application-manifest) ссылки.  
  
 Манифесты приложений для решений Office используют перечисленные ниже элементы и атрибуты [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] .  
  
|Элемент|Описание|Атрибуты|  
|-------------|-----------------|----------------|  
|[&#60;сборка&#62; элемент &#40;приложения ClickOnce&#41;](/visualstudio/deployment/assembly-element-clickonce-deployment)|Обязательный. Это элемент верхнего уровня.|**manifestVersion**|  
|[&#60;assemblyIdentity&#62; элемент &#40;приложения ClickOnce&#41;](/visualstudio/deployment/assemblyidentity-element-clickonce-deployment)|Обязательный. Определяет основную сборку приложения [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] .|**name**<br /><br /> **version**<br /><br /> **publicKeyToken**<br /><br /> **ProcessorArchitecture**<br /><br /> **language**|  
|[&#60;trustInfo&#62; элемент &#40;приложения ClickOnce&#41;](/visualstudio/deployment/trustinfo-element-clickonce-application)|Определяет требования к безопасности приложения.|Нет|  
|[&#60;entryPoint&#62; элемент &#40;приложения ClickOnce&#41;](/visualstudio/deployment/entrypoint-element-clickonce-application)|Обязательный. Определяет точку входа в код приложения для выполнения.|**name**<br /><br /> **dependencyName**<br /><br /> **customHostSpecified**|  
|[&#60;зависимость&#62; элемент &#40;приложения ClickOnce&#41;](/visualstudio/deployment/dependency-element-clickonce-deployment)|Обязательный. Определяет все зависимости, необходимые для выполнения приложения. При необходимости определяет сборки, которые требуется установить предварительно.|Нет|  
|[&#60;файл&#62; элемент &#40;приложения ClickOnce&#41;](/visualstudio/deployment/file-element-clickonce-application)|Обязательный. Определяет все не являющиеся сборками файлы, используемые приложением. Может включать данные изоляции модели COM, связанные с этим файлом.|**name**<br /><br /> **size**|  
  
 Манифесты приложений для решений Office имеют указанный ниже элемент в пространстве имен `co.v1` .  
  
```xml  
<entryPoint>  
    <co.v1:customHostSpecified />  
</entryPoint>   
```  
  
 Эти манифесты приложений также имеют в пространстве имен `vstav3` указанные ниже элементы и атрибуты.  
  
```xml  
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
|[&#60;customHostSpecified&#62; элемент &#40;разработка решений Office в Visual Studio&#41;](../vsto/customhostspecified-element-office-development-in-visual-studio.md)|Обязательный. Помечает манифест как решение Office.|Нет|  
|[&#60;ADDIN&#62; элемент &#40;разработка решений Office в Visual Studio&#41;](../vsto/addin-element-office-development-in-visual-studio.md)|Обязательный. Сохраняет точки входа в одном пространстве имен.|Нет|  
|[&#60;entryPointsCollection&#62; элемент &#40;разработка решений Office в Visual Studio&#41;](../vsto/entrypointscollection-element-office-development-in-visual-studio.md)|Обязательный. Группирует все сборки для одного или нескольких решений Office.|**id**|  
|[&#60;entryPoints&#62; элемент &#40;разработка решений Office в Visual Studio&#41;](../vsto/entrypoints-element-office-development-in-visual-studio.md)|Обязательный. Группирует все сборки для запуска решения Office.|Нет|  
|[&#60;entryPoint&#62; элемент &#40;разработка решений Office в Visual Studio&#41;](../vsto/entrypoint-element-office-development-in-visual-studio.md)|Обязательный. Указывает сборку, запускаемую в решении Office.|**class**<br /><br /> **Контракт**|  
|[&#60;Обновить&#62; элемент &#40;разработка решений Office в Visual Studio&#41;](../vsto/update-element-office-development-in-visual-studio.md)|Обязательный. Настраивает обновления для решения.|**включен**<br /><br /> **истечение срока действия**|  
|[&#60;postActions&#62; элемент &#40;разработка решений Office в Visual Studio&#41;](../vsto/postactions-element-office-development-in-visual-studio.md)|Необязательный параметр. Группирует все действия, выполняемые после развертывания, которые запускаются после установки решений Office.|Нет|  
|[&#60;postAction&#62; элемент &#40;разработка решений Office в Visual Studio&#41;](../vsto/postaction-element-office-development-in-visual-studio.md)|Необязательный параметр. Указывает действие, выполняемое после развертывания.|Нет|  
|[&#60;postActionData&#62; элемент &#40;разработка решений Office в Visual Studio&#41;](../vsto/postactiondata-element-office-development-in-visual-studio.md)|Необязательный параметр. Настраивает данные для действия, выполняемого после развертывания.|Нет|  
|[&#60;приложение&#62; элемент &#40;разработка решений Office в Visual Studio&#41;](../vsto/application-element-office-development-in-visual-studio.md)|Обязательный. Инкапсулирует сведения о приложении в один узел.|Нет|  
|[&#60;настройки&#62; элемент &#40;разработка решений Office в Visual Studio&#41;](../vsto/customizations-element-office-development-in-visual-studio.md)|Обязательный. Сохраняет все сведения о ведущем приложении в отдельном пространстве имен.|Нет|  
|[&#60;настройки&#62; элемент &#40;разработка решений Office в Visual Studio&#41;](../vsto/customization-element-office-development-in-visual-studio.md)|Обязательный. Сохраняет сведения о ведущем приложении в отдельном пространстве имен.|**xmlns**|  
|[&#60;документ&#62; элемент &#40;разработка решений Office в Visual Studio&#41;](../vsto/document-element-office-development-in-visual-studio.md)|Является обязательным только для решений на уровне документа. Хранит сведения о настройках.|**solutionId**|  
|[&#60;appAddin&#62; элемент &#40;разработка решений Office в Visual Studio&#41;](../vsto/appaddin-element-office-development-in-visual-studio.md)|Является обязательным только для решений на уровне приложения. Хранит сведения о настройках.|**Приложения**<br /><br /> **loadBehavior**<br /><br /> **keyName**|  
|[&#60;friendlyName&#62; элемент &#40;разработка решений Office в Visual Studio&#41;](../vsto/friendlyname-element-office-development-in-visual-studio.md)|Необязательный параметр. Хранит имя надстройки VSTO, которое будет отображаться в списке установленных надстроек VSTO.|Нет|  
|[&#60;Описание&#62; элемент &#40;разработка решений Office в Visual Studio&#41;](../vsto/description-element-office-development-in-visual-studio.md)|Является обязательным только для надстроек VSTO. Хранит описание, которое будет отображаться в списке установленных программ.|Нет|  
|[&#60;formRegions&#62; элемент &#40;разработка решений Office в Visual Studio&#41;](../vsto/formregions-element-office-development-in-visual-studio.md)|Является обязательным только для надстроек VSTO для Outlook, включающих области форм.|Нет|  
|[&#60;formRegion&#62; элемент &#40;разработка решений Office в Visual Studio&#41;](../vsto/formregion-element-office-development-in-visual-studio.md)|Является обязательным только для надстроек VSTO для Outlook, включающих области форм.|**Name**|  
|[&#60;vstoRuntime&#62; элемент &#40;разработка решений Office в Visual Studio&#41;](../vsto/vstoruntime-element-office-development-in-visual-studio.md)|Обязательный. Указывает конкретную версию среды выполнения средств Visual Studio для Office, поддерживаемую решением Office.|**release**<br /><br /> **version**<br /><br /> **supportUrl**|  
  
## <a name="remarks"></a>Примечания  
 Манифесты приложений и развертывания в решениях Office можно менять вручную. После этого нужно повторно подписать приложение и манифесты развертывания с помощью Manifest Generation and Editing Tool (*mage.exe* и *mageui.exe*). Дополнительные сведения см. в разделе [Как Повторное подписание манифестов приложения и развертывания](/visualstudio/deployment/how-to-re-sign-application-and-deployment-manifests).  
  
## <a name="file-location"></a>Расположение файла  
 Манифест приложения определяется для отдельной версии решения. По этой причине манифест приложения следует хранить отдельно от манифеста развертывания. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] помещает файлы, относящиеся к конкретной версии, в подкаталог, название которого соответствует версии и который находится в подкаталоге *Файлы приложения* каталога публикации.  
  
## <a name="file-name-syntax"></a>Синтаксис имени файла  
 Имя файла манифеста приложения должно быть полное имя и расширение приложения, как указано в **assemblyIdentity** элемент, с расширением *.manifest*. Например, манифест приложения, который ссылается на *OutlookAddIn1.dll* настройки используется следующий синтаксис имени файла.  
  
 `OutlookAddIn1.dll.manifest`  
  
## <a name="see-also"></a>См. также  
 [Манифесты развертывания для решений Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Манифест приложения ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  