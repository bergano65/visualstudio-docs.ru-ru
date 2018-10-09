---
title: 'Пошаговое руководство: Публикация расширения Visual Studio с помощью командной строки | Документация Майкрософт'
ms.custom: ''
ms.date: 07/12/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- publishing extensions
- extension, publishing
ms.assetid: 6ff9efc4-919d-4071-a80d-6dbdd2ceb2f8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8a915a8acdd9918f27a8909cdff2a790e6488566
ms.sourcegitcommit: b6dfa1bdf4c23c2e341754454bbd4758db2218e0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/08/2018
ms.locfileid: "48863908"
---
# <a name="walkthrough-publishing-a-visual-studio-extension-via-command-line"></a>Пошаговое руководство: Публикация расширения Visual Studio с помощью командной строки

В этом пошаговом руководстве показано, как для публикации расширения Visual Studio в Visual Studio Marketplace с помощью командной строки. При добавлении расширения в Marketplace, разработчики могут использовать [ **расширения и обновления** ](../ide/finding-and-using-visual-studio-extensions.md) диалоговое окно для поиска новых и обновленных расширений.

VsixPublisher.exe является средством командной строки для публикации расширений Visual Studio в Marketplace. Он может осуществляться из ${VSInstallDir}\VSSDK\VisualStudioIntegration\Tools\Bin\VsixPublisher.exe. Являются команд, доступных в это средство: **публикации**, **createPublisher**, **deletePublisher**, **deleteExtension**,  **Имя входа**, **выхода**.

## <a name="commands"></a>Команды

### <a name="publish"></a>publish

Публикует расширение в Marketplace. Расширение может быть vsix, exe или msi-файл или ссылку. Если расширение уже существует с той же версией, будут перезаписаны расширения. Если модуль еще не существует, он создаст новое расширение.

|Параметры команды                    |Описание:  |
|---------|---------|
|полезные данные (обязательно)                 |  Путь к полезные данные для публикации или ссылку для использования в качестве «Дополнительные сведения о URL-адрес».      |
|publishManifest (обязательно)         |  Файл для использования манифеста путь к публикации.       |
|ignoreWarnings                     |  Список предупреждений, чтобы игнорировать при публикации расширения. Эти предупреждения отображаются в виде командной строки сообщения при публикации расширения. (например, «VSIXValidatorWarning01, VSIXValidatorWarning02»)  
|personalAccesToken                 |  Личный маркер доступа, используемый для проверки подлинности издателя. Если не указано, личный маркер доступа запрашивается у вошедшего в систему пользователей.       |

```
VsixPublisher.exe publish -payload "{path to vsix}" -publishManifest "{path to vs-publish.json}" -ignoreWarnings "VSIXValidatorWarning01,VSIXValidatorWarning02"
```

### <a name="createpublisher"></a>createPublisher

Создает издатель в Marketplace. Также записывает издателя в машину для будущих действий (например, удаление и публикации расширения).

|Параметры команды                    |Описание:  |
|---------|---------|
|отображаемое имя (обязательно)             |  Отображаемое имя издателя.      |
|значение свойства publisherName (обязательно)           |  Имя издателя (например, идентификатор).      |
|personalAccessToken (обязательно)     |  Личный маркер доступа, используемый для проверки подлинности издателя.      |
|shortDescription                   |  Краткое описание издателя (а не файла).       |
|longDescription                    |  Подробное описание издателя (а не файла).      |

```
VsixPublisher.exe createPublisher -publisherName "{Publisher Name}" -displayName "{Publisher Display Name}" -personalAccessToken "{Personal Access Token}"
```

### <a name="deletepublisher"></a>deletePublisher

Удаление издателя в Marketplace.

|Параметры команды                    |Описание:  |
|---------|---------|
|значение свойства publisherName (обязательно)           |  Имя издателя (например, идентификатор).      |
|personalAccessToken (обязательно)     |  Личный маркер доступа, используемый для проверки подлинности издателя.      |

```
VsixPublisher.exe deletePublisher -publisherName "{Publisher Name}" -personalAccessToken "{Personal Access Token}"
```

### <a name="deleteextension"></a>deleteExtension

Удаление расширения из Marketplace.

|Параметры команды                    |Описание:  |
|---------|---------|
|extensionName (обязательно)           |  Имя расширения для удаления.      |
|значение свойства publisherName (обязательно)           |  Имя издателя (например, идентификатор).      |
|personalAccessToken                |  Личный маркер доступа, используемый для проверки подлинности издателя. Если не указано, личный маркер доступа запрашивается у вошедшего в систему пользователей.     |

```
VsixPublisher.exe deleteExtension -extensionName "{Extension Name}" -publisherName "{Publisher Name}"
```

### <a name="login"></a>Вход

Издатель вошедший в систему.

|Параметры команды                    |Описание:  |
|---------|---------|
|(требуется personalAccessToken      |  Личный маркер доступа, используемый для проверки подлинности издателя.      |
|значение свойства publisherName (обязательно)           |  Имя издателя (например, идентификатор).      |
|Перезаписать                          |  Указывает, перезаписи любого существующего издателя с новый личный маркер доступа.     |

```
VsixPublisher.exe login -personalAccessToken "{Personal Access Token}" -publisherName "{Publisher Name}"
```

### <a name="logout"></a>Выход из системы

Регистрирует издателя с компьютера.

|Параметры команды                    |Описание:  |
|---------|---------|
|значение свойства publisherName (обязательно)           |  Имя издателя (например, идентификатор).      |
|ignoreMissingPublisher             |  Указывает, что средство должна не ошибка, если указанный издатель не уже вошедшего в систему.     |

```
VsixPublisher.exe logout -publisherName "{Publisher Name}"
```

## <a name="publishmanifest-file"></a>файл publishManifest

Используется файл publishManifest **публикации** команды. Он представляет все метаданные о расширении, Marketplace необходимо знать. Если расширение передаваемая из расширения VSIX, свойство «identity» только должно иметь значение «внутреннееимя». Это обусловлено остальные свойства «identity» может быть создан из файла vsixmanifest. Если расширение msi и EXE-файлов или расширения ссылку, пользователь должен предоставить обязательные поля в свойстве «identity». Остальная часть манифест содержит сведения, относящиеся к Marketplace (например, категории, Q & A включения, и т.д.).

Пример файла publishManifest расширение VSIX.

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

MSI и EXE-файлов или ССЫЛКУ publishManifest образец файла:

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

## <a name="asset-files"></a>Файлы ресурсов

Файлы активов можно указать для внедрения таких вещей, как изображения в файле readme. Например, если расширение Markdown документ «Обзор»:

```markdown
TestExtension
...
This is test extension.
![Test logo](images/testlogo.png "Test logo")
```

Чтобы устранить «images/testlogo.png» в предыдущем примере, пользователь может предоставить «assetFiles» в их публикации манифеста как ниже:

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

## <a name="publishing-walkthrough"></a>Пошаговое руководство публикации

### <a name="prerequisites"></a>Предварительные требования

Для выполнения этого пошагового руководства необходимо установить пакет SDK для Visual Studio. Дополнительные сведения см. в разделе [установка Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

### <a name="create-a-visual-studio-extension"></a>Создание расширения Visual Studio

В этом случае мы будем использовать расширение VSPackage по умолчанию, но те же действия являются допустимыми для каждого типа расширений.

1. Создание пакета VSPackage в C# с именем «TestPublish» с командой меню. Дополнительные сведения см. в разделе [создание первого расширения: Hello World](../extensibility/extensibility-hello-world.md).

### <a name="package-your-extension"></a>Пакет расширения

1. Замените расширение vsixmanifest правильные сведения об имени продукта, автор и версии.

   ![Обновить расширение vsixmanifest](media/update-extension-vsixmanifest.png)

2. Построение расширения **выпуска** режим. Теперь расширение упаковываются в виде VSIX в папке \bin\Release.

3. Дважды щелкните VSIX для проверки установки.

### <a name="test-the-extension"></a>Тестирование расширения

 Перед распространением расширение построения и тестирования, чтобы убедиться, что он правильно установлен в экспериментальном экземпляре Visual Studio.

1. В Visual Studio начните отладку. Чтобы открыть экспериментальный экземпляр Visual Studio.

2. В экспериментальном экземпляре выберите **средства** меню и выберите пункт **расширения и обновления...** . Расширение TestPublish в центральной области появится и включить.

3. На **средства** меню, убедитесь, что вы видите команду теста.

### <a name="publish-the-extension-to-the-marketplace-via-command-line"></a>Публикация расширения в Marketplace с помощью командной строки

1. Убедитесь, что вы создавали версии расширения, и оно не устаревает.

2. Убедитесь, что вы создали файлы publishmanifest.json и overview.md.

3. Откройте командную строку и перейдите к каталогу \VSSDK\VisualStudioIntegration\Tools\Bin\ ${VSInstallDir}.

4. Чтобы создать новый издатель, используйте следующую команду:

   ```
   VsixPublisher.exe createPublisher -publisherName "TestVSIXPublisher" -displayName "Test VSIX Publisher" -personalAccessToken "{Personal Access Token that is used to authenticate the publisher. If not provided, the pat is acquired from the logged-in users.}"
   ```

5. При успешном создании издателя вы увидите следующее сообщение командной строки:

   ```
   Added 'Test VSIX Publisher' as a publisher on the Marketplace.
   ```

6. Можно проверить новый издатель вы создали, перейдя по адресу [Visual Studio Marketplace](https://marketplace.visualstudio.com/manage/publishers)

7. Чтобы опубликовать новое расширение, используйте следующую команду:

   ```
   VsixPublisher.exe publish -payload "{Path to vsix file}"  -publishManifest "{path to publishManifest file}"
   ```

8. При успешном создании издателя вы увидите следующее сообщение командной строки:

   ```
   Uploaded 'MyVsixExtension' to the Marketplace.
   ```

9. Вы можете проверить новое расширение, публикации, перейдя по адресу [Visual Studio Marketplace](https://marketplace.visualstudio.com/)

### <a name="install-the-extension-from-the-visual-studio-marketplace"></a>Установите расширение из Visual Studio Marketplace

Теперь, когда публикуется расширения, установите его в Visual Studio и протестируйте его.

1. В Visual Studio на **средства** меню, щелкните **расширения и обновления...** .

2. Нажмите кнопку **Online** и выполните поиск TestPublish.

3. Нажмите **Загрузить**. Затем расширение будет запланировано для установки.

4. Чтобы завершить установку, закройте все экземпляры Visual Studio.

## <a name="remove-the-extension"></a>Удаление расширения

Расширение можно удалить из Visual Studio Marketplace и на компьютере.

### <a name="to-remove-the-extension-from-the-marketplace-via-command-line"></a>Чтобы удалить расширение из Marketplace с помощью командной строки

1. Если вы хотите удалить расширение, используйте следующую команду:

   ```
   VsixPublisher.exe deleteExtension -publisherName "TestVSIXPublisher" -extensionName "MyVsixExtension"
   ```

2. Для успешного удаления расширения вы увидите следующее сообщение командной строки:

   ```
   Removed 'MyVsixExtension' from the Marketplace.
   ```

### <a name="to-remove-the-extension-from-your-computer"></a>Чтобы удалить расширение с компьютера

1. В Visual Studio на **средства** меню, щелкните **расширения и обновления...** .

2. Выберите «MyVsixExtension» и нажмите кнопку **удаления**. Расширения будут запланированы к удалению.

3. Чтобы завершить удаление, закройте все экземпляры Visual Studio.
