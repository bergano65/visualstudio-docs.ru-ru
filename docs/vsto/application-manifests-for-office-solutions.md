---
title: Манифесты приложений для решений Office
description: Узнайте, как манифест приложения — это XML-файл, описывающий сборки, загружаемые в Microsoft Office решение.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b3fbea6df2b66a108a048332e28a623bdaa95786
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99839032"
---
# <a name="application-manifests-for-office-solutions"></a>Манифесты приложений для решений Office
  Манифест приложения представляет собой XML-файл с описанием сборок, загружаемых в решении Microsoft Office. Средства разработки Microsoft Office в Visual Studio используют [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] схему манифеста приложения, определенную в справочнике по [манифесту приложения ClickOnce](../deployment/clickonce-application-manifest.md) .

 Манифесты приложений для решений Office используют перечисленные ниже элементы и атрибуты [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] .

|Элемент|Описание|Атрибуты|
|-------------|-----------------|----------------|
|[ Элемент&#62;&#60;сборки &#40;приложение ClickOnce&#41;](../deployment/assembly-element-clickonce-deployment.md)|Обязательный элемент. Это элемент верхнего уровня.|**манифестверсион**|
|[&#60;assemblyIdentity&#62; элемент &#40;приложение ClickOnce&#41;](../deployment/assemblyidentity-element-clickonce-deployment.md)|Обязательный элемент. Определяет основную сборку приложения [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] .|**name**<br /><br /> **version**<br /><br /> **publicKeyToken**<br /><br /> **processorArchitecture**<br /><br /> **language**|
|[&#60;trustInfo&#62; элемент &#40;приложение ClickOnce&#41;](../deployment/trustinfo-element-clickonce-application.md)|Определяет требования к безопасности приложения.|Отсутствуют|
|[&#60;entryPoint&#62; элемент &#40;приложение ClickOnce&#41;](../deployment/entrypoint-element-clickonce-application.md)|Обязательный элемент. Определяет точку входа в код приложения для выполнения.|**name**<br /><br /> **депенденцинаме**<br /><br /> **customHostSpecified**|
|[ Элемент&#62; зависимости&#60;&#40;приложение ClickOnce&#41;](../deployment/dependency-element-clickonce-deployment.md)|Обязательный элемент. Определяет все зависимости, необходимые для выполнения приложения. При необходимости определяет сборки, которые требуется установить предварительно.|Отсутствуют|
|[ Элемент&#62;&#60;файлов &#40;приложение ClickOnce&#41;](../deployment/file-element-clickonce-application.md)|Обязательный элемент. Определяет все не являющиеся сборками файлы, используемые приложением. Может включать данные изоляции модели COM, связанные с этим файлом.|**name**<br /><br /> **size**|

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
|[&#60;customHostSpecified&#62; элемент &#40;разработка решений Office в Visual Studio&#41;](../vsto/customhostspecified-element-office-development-in-visual-studio.md)|Обязательный элемент. Помечает манифест как решение Office.|Отсутствуют|
|[&#60;надстройки&#62; элемент &#40;разработка решений Office в Visual Studio&#41;](../vsto/addin-element-office-development-in-visual-studio.md)|Обязательный элемент. Сохраняет точки входа в одном пространстве имен.|Отсутствуют|
|[&#60;Ентрипоинтсколлектион&#62; элемент &#40;разработка решений Office в Visual Studio&#41;](../vsto/entrypointscollection-element-office-development-in-visual-studio.md)|Обязательный элемент. Группирует все сборки для одного или нескольких решений Office.|**id**|
|[&#60;EntryPoint&#62; элемент &#40;разработка решений Office в Visual Studio&#41;](../vsto/entrypoints-element-office-development-in-visual-studio.md)|Обязательный элемент. Группирует все сборки для запуска решения Office.|Отсутствуют|
|[&#60;entryPoint&#62; элемент &#40;разработке решений Office в Visual Studio&#41;](../vsto/entrypoint-element-office-development-in-visual-studio.md)|Обязательный элемент. Указывает сборку, запускаемую в решении Office.|**class**<br /><br /> **архивирован**|
|[&#60;обновление&#62; элемента &#40;разработке решений Office в Visual Studio&#41;](../vsto/update-element-office-development-in-visual-studio.md)|Обязательный элемент. Настраивает обновления для решения.|**доступной**<br /><br /> **expiration**|
|[&#60;действия&#62; элемента &#40;разработке решений Office в Visual Studio&#41;](../vsto/postactions-element-office-development-in-visual-studio.md)|Необязательный элемент. Группирует все действия, выполняемые после развертывания, которые запускаются после установки решений Office.|Отсутствуют|
|[ Элемент&#62;&#60;действия &#40;разработки Office в Visual Studio&#41;](../vsto/postaction-element-office-development-in-visual-studio.md)|Необязательный элемент. Указывает действие, выполняемое после развертывания.|Отсутствуют|
|[&#60;Постактиондата&#62; элемент &#40;разработка решений Office в Visual Studio&#41;](../vsto/postactiondata-element-office-development-in-visual-studio.md)|Необязательный элемент. Настраивает данные для действия, выполняемого после развертывания.|Отсутствуют|
|[ Элемент&#62; приложения&#60;&#40;разработки Office в Visual Studio&#41;](../vsto/application-element-office-development-in-visual-studio.md)|Обязательный элемент. Инкапсулирует сведения о приложении в один узел.|Отсутствуют|
|[&#60;настройки&#62; элемента &#40;разработке решений Office в Visual Studio&#41;](../vsto/customizations-element-office-development-in-visual-studio.md)|Обязательный элемент. Сохраняет все сведения о ведущем приложении в отдельном пространстве имен.|Отсутствуют|
|[ Элемент&#62; настройки&#60;&#40;разработке решений Office в Visual Studio&#41;](../vsto/customization-element-office-development-in-visual-studio.md)|Обязательный элемент. Сохраняет сведения о ведущем приложении в отдельном пространстве имен.|**xmlns**|
|[&#60;элемента&#62; документа &#40;разработке решений Office в Visual Studio&#41;](../vsto/document-element-office-development-in-visual-studio.md)|Является обязательным только для решений на уровне документа. Хранит сведения о настройках.|**solutionId**|
|[&#60;Аппаддин&#62; элемент &#40;разработка решений Office в Visual Studio&#41;](../vsto/appaddin-element-office-development-in-visual-studio.md)|Является обязательным только для решений на уровне приложения. Хранит сведения о настройках.|**приложение**<br /><br /> **loadBehavior**<br /><br /> **keyName**|
|[&#60;friendlyName&#62; элемент &#40;разработка решений Office в Visual Studio&#41;](../vsto/friendlyname-element-office-development-in-visual-studio.md)|Необязательный элемент. Хранит имя надстройки VSTO, которое будет отображаться в списке установленных надстроек VSTO.|Отсутствуют|
|[&#60;описание&#62; элемента &#40;разработке решений Office в Visual Studio&#41;](../vsto/description-element-office-development-in-visual-studio.md)|Требуется только для надстроек VSTO. Содержит описание, которое отображается в списке установленных программ.|Отсутствуют|
|[&#60;Формрегионс&#62; элемент &#40;разработка решений Office в Visual Studio&#41;](../vsto/formregions-element-office-development-in-visual-studio.md)|Является обязательным только для надстроек VSTO для Outlook, включающих области форм.|Отсутствуют|
|[&#60;Формрегион&#62; элемент &#40;разработка решений Office в Visual Studio&#41;](../vsto/formregion-element-office-development-in-visual-studio.md)|Является обязательным только для надстроек VSTO для Outlook, включающих области форм.|**Имя**|
|[&#60;Всторунтиме&#62; элемент &#40;разработка решений Office в Visual Studio&#41;](../vsto/vstoruntime-element-office-development-in-visual-studio.md)|Обязательный элемент. Указывает конкретную версию среды выполнения средств Visual Studio для Office, поддерживаемую решением Office.|**отпускании**<br /><br /> **version**<br /><br /> **supportUrl;**|

## <a name="remarks"></a>Remarks
 Манифесты приложений и развертывания в решениях Office можно менять вручную. Затем необходимо повторно подписать манифесты приложения и развертывания с помощью Инструмент создания и изменения манифестов (*mage.exe* и *mageui.exe*). Дополнительные сведения см. [в разделе как повторно подписывать манифесты приложения и развертывания](../deployment/how-to-re-sign-application-and-deployment-manifests.md).

## <a name="file-location"></a>Размещение файла
 Манифест приложения определяется для отдельной версии решения. По этой причине манифест приложения следует хранить отдельно от манифеста развертывания. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] помещает файлы конкретной версии в подкаталог, названный после соответствующей версии, в подкаталог *файлы приложения* в папке Publish.

## <a name="file-name-syntax"></a>Синтаксис имени файла
 Имя файла манифеста приложения должно быть полным именем и расширением приложения, определенным в элементе **assemblyIdentity** , за которым следует расширение *manifest*. Например, манифест приложения, который ссылается на настройку *OutlookAddIn1.dll* , будет использовать следующий синтаксис имени файла.

 `OutlookAddIn1.dll.manifest`

## <a name="see-also"></a>См. также раздел

- [Манифесты развертывания для решений Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md)