---
title: Создайте пакет расширений с шаблоном элемента пакета расширения (ru) Документы Майкрософт
ms.date: 07/27/2018
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: 5388EEBA-211D-4114-8CD9-70C899919F7E
author: acangialosi
ms.author: anthc
manager: Meng
ms.workload:
- vssdk
ms.openlocfilehash: fa1c141e18a3870eaad4b155d816e30ee207f45d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697748"
---
# <a name="walkthrough-create-an-extension-pack"></a>Пошаговое руководство. Создание пакета расширения

Пакет расширения представляет собой набор расширений, которые могут быть установлены вместе. Пакеты расширений позволяют легко делиться любимыми расширениями с другими пользователями или объединять набор расширений для конкретного сценария.

## <a name="prerequisites"></a>Предварительные требования

Начиная с Visual Studio 2015, Visual Studio SDK включен в качестве дополнительной функции в установке Visual Studio. Вы также можете установить VS SDK позже. Для получения дополнительной информации, см [Установка Визуальной студии SDK](../extensibility/installing-the-visual-studio-sdk.md).

Функция расширения Pack доступна начиная с Visual Studio 15.8 Предварительный просмотр 2.

## <a name="create-an-extension-with-an-extension-pack-item-template"></a>Создание расширения с шаблоном элемента пакета расширения

Шаблон элемента пакета расширения создает пакет расширений с набором расширений, которые могут быть установлены вместе.

1. В диалоге **нового проекта** ищите "vsix" и выберите **проект VSIX.** Для **названия проекта**введите тип "Пакет расширения тестирования". Нажмите кнопку **создания**.

2. В **Solution Explorer**, правой кнопкой мыши узла проекта и выберите **Добавить** > **новый пункт**. Перейдите к узлом **расширения** визуальных элементов ИК и выберите **пакет расширения.** Оставьте имя файла по умолчанию (ExtensionPack1.cs).

3. Добавлен файл ExtensionPack1.vsext, содержащий следующий код

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

4. Vsixid расширения, чтобы включить в расширение Pack можно найти на [Visual Studio Marketplace](https://marketplace.visualstudio.com/). Найдите расширение, включаевщее и нажмите на **Copy ID.** Вы можете обновить существующий **vsixId** в вышеуказанном файле или добавить еще одно расширение в список.

    ![Копия VsixId с рынка](media/vsixid-marketplace.png)

5. Создайте проект и загрузите расширение на Marketplace. Смотрите [Публикация расширения Визуальной студии](../extensibility/walkthrough-publishing-a-visual-studio-extension.md).

> [!NOTE]
> Пакет расширения может устанавливать только расширения, доступные на [Visual Studio Marketplace](https://marketplace.visualstudio.com/) или [частной галерее.](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md)

## <a name="install-the-extension-pack-from-the-visual-studio-marketplace"></a>Установите пакет расширений с рынка визуальной студии

Теперь, когда расширение опубликовано, установите его в Visual Studio и протестируйте его там.

::: moniker range="vs-2017"

1. В Visual Studio, в меню **Инструментов,** нажмите **расширения и обновления**.

::: moniker-end

::: moniker range=">=vs-2019"

1. В Visual Studio, в меню **расширений,** нажмите **Управляемые расширения**.

::: moniker-end

2. Нажмите **онлайн,** а затем поиск "Тест расширение pack".

3. Щелкните элемент **Загрузить**. Расширение и список расширений, включенных в пакет расширения, будут запланированы для установки.

4. Ниже приведен пример расширения пакет скачать представление **диалог управления расширениями.** Если вы предпочитаете установить только некоторые из включенных расширений в пакет расширения, вы можете изменить список расширений в **запланированном для установки.**

    ![Скачать пакет расширения от Marketplace](media/vside-extensionpack.png)

5. Для завершения установки закройте все экземпляры Visual Studio.

## <a name="remove-the-extension"></a>Удаление расширения

Чтобы удалить расширение с компьютера:

::: moniker range="vs-2017"

1. В Visual Studio, в меню **Инструментов,** нажмите **расширения и обновления**.

::: moniker-end

::: moniker range=">=vs-2019"

1. В Visual Studio, в меню **расширений,** нажмите **Управляемые расширения**.

::: moniker-end

2. Выберите **пакет расширения теста,** а затем нажмите **Uninstall.** Расширение и список расширений, включенных в пакет расширения, будут запланированы для удаления.

3. Чтобы завершить неустановку, закройте все экземпляры Visual Studio.
