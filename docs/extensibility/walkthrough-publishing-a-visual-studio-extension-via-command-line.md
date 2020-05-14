---
title: Опубликовать расширение с помощью командной строки
ms.date: 07/12/2018
ms.topic: conceptual
helpviewer_keywords:
- publishing extensions
- extension, publishing
ms.assetid: 6ff9efc4-919d-4071-a80d-6dbdd2ceb2f8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 40be0252218f39b4ff98b58caedd7f9f20ce6d5d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697131"
---
# <a name="walkthrough-publishing-a-visual-studio-extension-via-command-line"></a>Прохождение: Публикация расширения Visual Studio через командную строку

В этом пошаговом слове показано, как опубликовать расширение Visual Studio на Visual Studio Marketplace с помощью командной строки. При добавлении расширения в Marketplace разработчики могут использовать диалог [**расширений и обновлений**](../ide/finding-and-using-visual-studio-extensions.md) для просмотра новых и обновленных расширений.

VsixPublisher.exe является инструментом командной строки для публикации расширений Visual Studio на Marketplace. К нему можно получить доступ по электронной информации по сайтам VSInstallDir (VSSDK)VsSDK-VisualStudioIntegration-Инструменты -Bin-VsixPublisher.exe. Команды доступны на этом инструменте: **публиковать**, **создаватьPublisher**, **deletePublisher**, **deleteExtension**, **войти**в систему , **выйти**.

## <a name="commands"></a>Команды

### <a name="publish"></a>Опубликовать

Публикует расширение marketplace. Расширение может быть vsix, exe/msi файл, или ссылка. Если расширение уже существует с той же версией, оно перезапишет расширение. Если расширение еще не существует, это создаст новое расширение.

|Параметры командования |Описание |
|---------|---------|
|полезная нагрузка (требуется) | Либо путь к полезной нагрузке для публикации, либо ссылка для использования в качестве "больше информации URL". |
|ПубликацияManifest (требуется) | Путь к файлу манифеста публикации для использования. |
|игнорироватьПредупреждения | Список предупреждений, которые можно игнорировать при публикации расширения. Эти предупреждения отображаются как сообщения командной строки при публикации расширения. (например, "VSIXValidatorWarning01, VSIXValidatorWarning02")
|личныйAccessToken | Токен personal Access (PAT), используемый для аутентификации издателя. Если это не предусмотрено, PAT приобретается у зарегистрированных пользователей. |

```
VsixPublisher.exe publish -payload "{path to vsix}" -publishManifest "{path to vs-publish.json}" -ignoreWarnings "VSIXValidatorWarning01,VSIXValidatorWarning02"
```

### <a name="createpublisher"></a>создатьИздатель

Создает издателя на Marketplace. Также регистрирует издателя в машине для будущих действий (например, удаляя/опубликовывая расширение).

|Параметры командования |Описание |
|---------|---------|
|name дисплея (требуется) | Отобразить имя издателя. |
|publisherName (требуется) | Имя издателя (например, идентификатор). |
|personalAccessToken (требуется) | Токен personal Access, используемый для аутентификации издателя. |
|shortDescription | Краткое описание издателя (не файл). |
|долгоОписание | Длинное описание издателя (не файл). |

```
VsixPublisher.exe createPublisher -publisherName "{Publisher Name}" -displayName "{Publisher Display Name}" -personalAccessToken "{Personal Access Token}"
```

### <a name="deletepublisher"></a>удалитьИздателя

Удаляет издателя на Marketplace.

|Параметры командования |Описание |
|---------|---------|
|publisherName (требуется) | Имя издателя (например, идентификатор). |
|personalAccessToken (требуется) | Токен personal Access, используемый для аутентификации издателя. |

```
VsixPublisher.exe deletePublisher -publisherName "{Publisher Name}" -personalAccessToken "{Personal Access Token}"
```

### <a name="deleteextension"></a>deleteExtension

Удаляет расширение из Marketplace.

|Параметры командования |Описание |
|---------|---------|
|extensionName (требуется) | Название расширения для удаления. |
|publisherName (требуется) | Имя издателя (например, идентификатор). |
|личныйAccessToken | Токен personal Access, используемый для аутентификации издателя. Если это не предусмотрено, погладить приобретается у зарегистрированных пользователей. |

```
VsixPublisher.exe deleteExtension -extensionName "{Extension Name}" -publisherName "{Publisher Name}"
```

### <a name="login"></a>login

Входы издателя в машину.

|Параметры командования |Описание |
|---------|---------|
|personalAccessToken (требуется | Токен personal Access, используемый для аутентификации издателя. |
|publisherName (требуется) | Имя издателя (например, идентификатор). |
|overwrite | Упомяните, что любой существующий издатель должен быть перезаписан с новым токеном для личного доступа. |

```
VsixPublisher.exe login -personalAccessToken "{Personal Access Token}" -publisherName "{Publisher Name}"
```

### <a name="logout"></a>logout

Входит в систему издателя из машины.

|Параметры командования |Описание |
|---------|---------|
|publisherName (требуется) | Имя издателя (например, идентификатор). |
|ignoreMissingPublisher | Уточняется, что инструмент не должен ошибаться, если указанный издатель еще не зарегистрирован. |

```
VsixPublisher.exe logout -publisherName "{Publisher Name}"
```

## <a name="publishmanifest-file"></a>Опубликоватьфайл

Файл publishManifest используется командой **публикации.** Он представляет все метаданные о расширении, что Marketplace должен знать. Если загруженное расширение происходит из расширения VSIX, свойство "идентификация" должно иметь только набор "internalName". Это связано с тем, что остальные свойства "идентичности" могут быть сгенерированы из файла vsixmanifest. Если расширение является msi/exe или расширением ссылки, пользователь должен предоставить требуемые поля в свойстве "идентификация". Остальная часть манифеста содержит информацию, специфичную для Marketplace (например, категории, включена ли&А и т.д.).

Расширение VSIX публикуетManifest образец файла:

```json
{
    "$schema": "http://json.schemastore.org/vsix-publish",
    "categories": [ "build", "coding" ],  // The categories of the extension. Between 1 and 3 categories are required.
    "identity": {
        "internalName": "MyVsixExtension" // If not specified, we try to generate the name from the display name of the extension in the vsixmanifest file.
                                            // Required if the display name is not the actual name of the extension.
    },
    "overview": "overview.md",            // Path to the "readme" file that gets uploaded to the Marketplace. Required.
    "priceCategory": "free",              // Either "free", "trial", or "paid". Defaults to "free".
    "publisher": "MyPublisherName",       // The name of the publisher. Required.
    "private": false,                     // Specifies whether or not the extension should be public when uploaded. Defaults to false.
    "qna": true,                          // Specifies whether or not the extension should have a Q&A section. Defaults to true.
    "repo": "https://github.com/MyPublisherName/MyVsixExtension" // Not required.
}
```

MSI/EXE или LINK публикуют пробную выборку файлов:

```json
{
    "$schema": "http://json.schemastore.org/vsix-publish",
    "categories": [ "build", "coding" ],
    "identity": {
        "description": "My extension.", // The description of the extension. Required for non-vsix extensions.
        "displayName": "My Extension",  // The display name of the extension. Required for non-vsix extensions.
        "icon": "\\path\\to\\icon.ico", // The path to an icon file (can be relative to the json file location). Required for non-vsix extensions.
        "installTargets": [             // The installation targets for the extension. Required for non-vsix extensions.
            {
                "sku": "Microsoft.VisualStudio.Community",
                "version": "[10.0, 16.0)"
            }
        ],
        "internalName": "MyExtension",
        "language": "en-US",            // The default language id of the extension. Can be in the "1033" or "en-US" format. Required for non-vsix extensions.
        "tags": [ "tag1", "tag2" ],     // The tags for the extension. Not required.
        "version": "3.7.0",             // The version of the extension. Required for non-vsix extensions.
        "vsixId": "MyExtension",        // The vsix id of the extension. Not required but useful for showing updates to installed extensions.
    },
    "overview": "overview.md",
    "priceCategory": "free",
    "publisher": "MyPublisherName",
    "private": false,
    "qna": true,
    "repo": "https://github.com/MyPublisherName/MyVsixExtension"
}
```

## <a name="asset-files"></a>Файлы активов

Файлы активов могут быть предоставлены для встраивания таких вещей, как изображения в файл есчитых. Например, если в расширении есть следующий документ "Обзор" Markdown:

```markdown
TestExtension
...
This is test extension.
![Test logo](images/testlogo.png "Test logo")
```

Для того, чтобы решить "изображения / testlogo.png" в предыдущем примере, пользователь может предоставить "assetFiles" в их публикации манифест, как ниже:

```json
{
    "assetFiles": [
        {
            "pathOnDisk": "\\path\\to\\logo.png",
            "targetPath": "images/logo.png"
        }
    ],
    // other required fields
}
```

## <a name="publishing-walkthrough"></a>Публикация пошагового

### <a name="prerequisites"></a>Предварительные требования

Для выполнения этого пошагового руководства необходимо установить пакет SDK для Visual Studio. Для получения дополнительной информации, см [Установка Визуальной студии SDK](../extensibility/installing-the-visual-studio-sdk.md).

### <a name="create-a-visual-studio-extension"></a>Создание расширения Visual Studio

В этом случае мы будем использовать расширение VSPackage по умолчанию, но одни и те же шаги действительны для каждого вида расширения.

1. Создайте VSPackage в C е под названием "TestPublish", который имеет команду меню. Для получения дополнительной информации [см.](../extensibility/extensibility-hello-world.md)

### <a name="package-your-extension"></a>Упаковка расширения

1. Обновление расширения vsixmanifest с правильной информацией о названии продукта, авторе и версии.

   ![обновление расширения vsixmanifest](media/update-extension-vsixmanifest.png)

2. Создайте расширение в режиме **выпуска.** Теперь ваше расширение будет упаковано в качестве VSIX в папку «Бин»Release.

3. Вы можете дважды щелкнуть VSIX для проверки установки.

### <a name="test-the-extension"></a>Проверьте расширение

 Перед тем, как распределить расширение, построить и протестировать его, чтобы убедиться, что он установлен правильно в экспериментальном экземпляре Visual Studio.

1. В Visual Studio начните отладку. открыть экспериментальный экземпляр Visual Studio.

2. В экспериментальном примере перейдите в меню **Tools** и нажмите **расширения и обновления...**. Расширение TestPublish должно отображаться в центральном стене и быть включенным.

3. В меню **«Инструменты»** убедитесь, что вы видите тестовую команду.

### <a name="publish-the-extension-to-the-marketplace-via-command-line"></a>Опубликовать расширение marketplace через командную строку

1. Убедитесь, что вы создали версию релиза вашего расширения и что она актуальна.

2. Убедитесь, что вы создали publishmanifest.json и overview.md файлов.

3. Откройте командную строку и перейдите в каталог «VSInstallDir» (VSSDK)ВизуальнаястудияИнтеграция/Инструменты и Бин».

4. Чтобы создать нового издателя, используйте следующую команду:

   ```
   VsixPublisher.exe createPublisher -publisherName "TestVSIXPublisher" -displayName "Test VSIX Publisher" -personalAccessToken "{Personal Access Token that is used to authenticate the publisher. If not provided, the pat is acquired from the logged-in users.}"
   ```

5. При успешном создании издателя вы увидите следующее сообщение командной строки:

   ```
   Added 'Test VSIX Publisher' as a publisher on the Marketplace.
   ```

6. Вы можете проверить нового издателя, созданного вами, перенаправившись в [Visual Studio Marketplace](https://marketplace.visualstudio.com/manage/publishers)

7. Чтобы опубликовать новое расширение, используйте следующую команду:

   ```
   VsixPublisher.exe publish -payload "{Path to vsix file}"  -publishManifest "{path to publishManifest file}"
   ```

8. При успешном создании издателя вы увидите следующее сообщение командной строки:

   ```
   Uploaded 'MyVsixExtension' to the Marketplace.
   ```

9. Вы можете проверить новое расширение, опубликованное вами, перемещаясь по [Visual Studio Marketplace](https://marketplace.visualstudio.com/)

### <a name="install-the-extension-from-the-visual-studio-marketplace"></a>Установите расширение с рынка визуальной студии

Теперь, когда расширение опубликовано, установите его в Visual Studio и протестируйте его там.

1. В Visual Studio, в меню **Инструменты,** нажмите **расширения и обновления ...**.

2. Нажмите **онлайн,** а затем поиск TestPublish.

3. Щелкните элемент **Загрузить**. Затем будет запланирована установка расширения.

4. Для завершения установки закройте все экземпляры Visual Studio.

## <a name="remove-the-extension"></a>Удаление расширения

Вы можете удалить расширение из Visual Studio Marketplace и с вашего компьютера.

### <a name="to-remove-the-extension-from-the-marketplace-via-command-line"></a>Удаление расширения с Marketplace через командную строку

1. Если требуется удалить расширение, используйте следующую команду:

   ```
   VsixPublisher.exe deleteExtension -publisherName "TestVSIXPublisher" -extensionName "MyVsixExtension"
   ```

2. При успешном удалении расширения вы увидите следующее сообщение командной строки:

   ```
   Removed 'MyVsixExtension' from the Marketplace.
   ```

### <a name="to-remove-the-extension-from-your-computer"></a>Удаление расширения с компьютера

1. В Visual Studio, в меню **Инструментов,** нажмите **расширения и обновления**.

2. Выберите "MyVsixExtension", а затем нажмите **Uninstall**. Затем расширение будет запланировано для удаления.

3. Чтобы завершить неустановку, закройте все экземпляры Visual Studio.
