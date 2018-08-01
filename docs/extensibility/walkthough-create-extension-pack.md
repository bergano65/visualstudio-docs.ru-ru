---
title: Создание пакета расширения с помощью шаблона элемента пакета расширения | Документация Майкрософт
ms.custom: ''
ms.date: 07/27/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: 5388EEBA-211D-4114-8CD9-70C899919F7E
author: chitray
ms.author: chitray
manager: Meng
ms.workload:
- vssdk
ms.openlocfilehash: f87f359d9c143adc9093b08ef58ebca89dca524e
ms.sourcegitcommit: ed524fd809b17ad1d06bf9cd4c3374c71a44d7bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/01/2018
ms.locfileid: "39409917"
---
# <a name="walkthrough-create-an-extension-pack"></a>Пошаговое руководство по Созданию пакета расширения

Пакет расширения — это набор расширений, которые могут быть установлены вместе. Пакеты расширения позволяют легко поделиться избранные расширения с другими пользователями или объединить набор расширений для конкретного сценария.
  
## <a name="prerequisites"></a>Предварительные требования

Начиная с Visual Studio 2015, не следует устанавливать пакет SDK для Visual Studio из центра загрузки. Она будет включена в качестве дополнительного компонента в программе установки Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [установка Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  

Функция Extension Pack доступен, начиная с Visual Studio 15.8 предварительной версии 2.
  
## <a name="create-an-extension-with-an-extension-pack-item-template"></a>Создание расширения с помощью шаблона элемента Extension Pack

Шаблон элемента Extension Pack создает пакет расширения с помощью набора расширений, которые могут быть установлены вместе.
  
1. В **новый проект** диалогового окна разверните узел **Visual C#** или **Visual Basic** и нажмите кнопку **расширяемости**. В **шаблоны** области выберите **проект VSIX**. В поле **Имя** введите `Test Extension Pack`. Нажмите кнопку **ОК**.  
  
2. В **обозревателе решений**, щелкните правой кнопкой мыши узел проекта и выберите **добавить / новый элемент**. Перейдите в Visual C# **расширяемости** узел и выберите **пакет расширений**. Оставьте имя файла по умолчанию (ExtensionPack1.cs).  
  
3. Добавляется файл ExtensionPack1.vsext, который содержит следующий код

  ```json
  {
    "id": "ExtensionPack1",
    "name": "ExtensionPack1",
    "description": "Read about creating extension packs at https://aka.ms/vsextpack",
    "version": "1.0.0.0",
    "extensions": [  // List of extensions that are included in the Extension Pack.
      {
        "vsixId": "41858b2d-ff0b-4a43-80b0-f1b2d6084935", // The vsix id of the extension you want to   include.
        "name": "AlignAssignments"
      },
      {
          "vsixId": "42374550-426a-400e-96f9-237682e8dea6",
        "name": "CopyAsHtml"
      }
    ]
  }  
  ```

4. Vsixid расширения для включения в пакет расширений можно найти на [Visual Studio Marketplace](https://marketplace.visualstudio.com/). Найдите нужное расширение и нажмите кнопку на **идентификатор копирования**. Вы можете обновить существующий **vsixId** выше файл или добавить другое расширение в список.

    ![Скопируйте VsixId из Marketplace](media/vsixid-marketplace.png)

5. Постройте проект и отправки расширения в Marketplace. См. в разделе [публикация расширения Visual Studio](../extensibility/walkthrough-publishing-a-visual-studio-extension.md). 
    
> [!NOTE]
> Пакет расширения можно установить только расширения, доступные на [Visual Studio Marketplace](https://marketplace.visualstudio.com/) или [частной коллекции](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md).
 
## <a name="install-the-extension-pack-from-the-visual-studio-marketplace"></a>Установить пакет расширений в Visual Studio Marketplace

Теперь, когда публикуется расширения, установите его в Visual Studio и протестируйте его.

1. В Visual Studio на **средства** меню, щелкните **расширения и обновления...** .

2. Нажмите кнопку **Online** и выполните поиск `Test Extension Pack`.

3. Нажмите **Загрузить**. Расширение и свой список расширений, входящих в пакет расширений будет затем запланировано для установки.

4. Ниже приведено представление загрузки пакет расширений образец **расширения и обновления** диалоговое окно. Если вы хотите установить только некоторые расширения включены в пакет расширений, можно изменить список расширений в **запланировано для установки**.

    ![Загрузить пакет расширения из Marketplace](media/vside-extensionpack.png)

5. Чтобы завершить установку, закройте все экземпляры Visual Studio.

## <a name="remove-the-extension"></a>Удаление расширения

Чтобы удалить расширение с компьютера:

1. В Visual Studio на **средства** меню, щелкните **расширения и обновления...** .

2. Выберите `Test Extension Pack` и нажмите кнопку **удаления**. Расширение и свой список расширений, входящих в пакет расширений будет затем запланировано для удаления.

3. Чтобы завершить удаление, закройте все экземпляры Visual Studio.
