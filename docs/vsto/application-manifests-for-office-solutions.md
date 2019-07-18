---
title: Манифесты приложений для решений Office
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 62ad6a8147fc11b8bed34605b6447a1fe8a62a97
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62942927"
---
# <a name="application-manifests-for-office-solutions"></a>Манифесты приложений для решений Office
  Манифест приложения представляет собой XML-файл с описанием сборок, загружаемых в решении Microsoft Office. Средства разработки Microsoft Office в Visual Studio используют [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] схему манифестов приложений, определенных в [манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md) ссылки.

 Манифесты приложений для решений Office используют перечисленные ниже элементы и атрибуты [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] .

|Элемент|Описание|Атрибуты|
|-------------|-----------------|----------------|
|[&#60;сборка&#62; элемент &#40;приложения ClickOnce&#41;](../deployment/assembly-element-clickonce-deployment.md)|Обязательный. Это элемент верхнего уровня.|**manifestVersion**|
|[&#60;assemblyIdentity&#62; элемент &#40;приложения ClickOnce&#41;](../deployment/assemblyidentity-element-clickonce-deployment.md)|Обязательный. Определяет основную сборку приложения [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] .|**name**<br /><br /> **version**<br /><br /> **publicKeyToken**<br /><br /> **ProcessorArchitecture**<br /><br /> **language**|
|[&#60;trustInfo&#62; элемент &#40;приложения ClickOnce&#41;](../deployment/trustinfo-element-clickonce-application.md)|Определяет требования к безопасности приложения.|Нет|
|[&#60;entryPoint&#62; элемент &#40;приложения ClickOnce&#41;](../deployment/entrypoint-element-clickonce-application.md)|Обязательный. Определяет точку входа в код приложения для выполнения.|**name**<br /><br /> **dependencyName**<br /><br /> **customHostSpecified**|
|[&#60;зависимость&#62; элемент &#40;приложения ClickOnce&#41;](../deployment/dependency-element-clickonce-deployment.md)|Обязательный. Определяет все зависимости, необходимые для выполнения приложения. При необходимости определяет сборки, которые требуется установить предварительно.|Нет|
|[&#60;файл&#62; элемент &#40;приложения ClickOnce&#41;](../deployment/file-element-clickonce-application.md)|Обязательный. Определяет все не являющиеся сборками файлы, используемые приложением. Может включать данные изоляции модели COM, связанные с этим файлом.|**name**<br /><br /> **size**|

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
 Манифесты приложений и развертывания в решениях Office можно менять вручную. После этого нужно повторно подписать приложение и манифесты развертывания с помощью Manifest Generation and Editing Tool (*mage.exe* и *mageui.exe*). Дополнительные сведения см. в разделе [Как повторно подписать манифесты приложения и развертывания](../deployment/how-to-re-sign-application-and-deployment-manifests.md).

## <a name="file-location"></a>Расположение файла
 Манифест приложения определяется для отдельной версии решения. По этой причине манифест приложения следует хранить отдельно от манифеста развертывания. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] помещает файлы, относящиеся к конкретной версии, в подкаталог, название которого соответствует версии и который находится в подкаталоге *Файлы приложения* каталога публикации.

## <a name="file-name-syntax"></a>Синтаксис имени файла
 Имя файла манифеста приложения должно быть полное имя и расширение приложения, как указано в **assemblyIdentity** элемент, с расширением *.manifest*. Например, манифест приложения, который ссылается на *OutlookAddIn1.dll* настройки используется следующий синтаксис имени файла.

 `OutlookAddIn1.dll.manifest`

## <a name="see-also"></a>См. также

- [Манифесты развертывания для решений Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md)