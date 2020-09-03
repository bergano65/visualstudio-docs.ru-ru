---
title: Пошаговое руководство. Создание настраиваемого редактора | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], custom - create
ms.assetid: d090abb6-d99f-4083-a3db-cd16bf81ce7d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4713931d70fd91dd57b85bc6fc749e62e03eb20b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85905920"
---
# <a name="walkthrough-create-a-custom-editor"></a>Пошаговое руководство. Создание пользовательского редактора
Шаблон проекта VSPackage может создавать простой пользовательский редактор в C++. Шаблон проекта VSPackage больше не поддерживает проекты C# и Visual Basic. Дополнительные сведения см. в разделе [пакет SDK для Visual Studio](../extensibility/visual-studio-sdk.md).

## <a name="prerequisites"></a>Предварительные требования
 Для выполнения этого пошагового руководства необходимо установить пакет SDK для Visual Studio. Дополнительные сведения см. [в статье Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="the-visual-studio-package-project-template"></a>Шаблон проекта пакета Visual Studio
 Шаблон проекта пакета Visual Studio можно найти в диалоговом окне **Новый проект** в папке **расширяемость C++** .

### <a name="to-create-a-vspackage-using-the-visual-studio-package-template"></a>Создание VSPackage с помощью шаблона пакета Visual Studio

1. Создайте проект с помощью шаблона пакета Visual Studio.

2. Выберите параметр **Пользовательский редактор** и нажмите кнопку **Далее**. Откроется страница **Параметры редактора** .

3. Введите имя редактора в поле **имя редактора** . Введите расширение файла, которое необходимо связать с редактором, в поле **расширение файла** . Редактор доступен для файлов с этим расширением. Расширение файла регистрируется только для Visual Studio, а не для Windows. Введите имя файла по умолчанию для новых документов, созданных с помощью редактора, в поле **Default File Name (имя файла по умолчанию** ).

4. Нажмите кнопку **Готово** , чтобы создать VSPackage в указанной папке.

### <a name="to-test-your-custom-editor"></a>Тестирование пользовательского редактора

1. В меню **файл** наведите указатель мыши на пункт **создать** и выберите **файл**.

2. В области **Установленные шаблоны** диалогового окна **новый файл** выберите шаблон файла, а затем зарегистрированный тип файла.

3. Нажмите кнопку **Открыть** , чтобы просмотреть и изменить документ.

     Редактор поддерживает операции копирования и вставки, поиска и замены, а также операций открытия и загрузки.

## <a name="see-also"></a>См. также раздел
- [VSPackages](../extensibility/internals/vspackages.md)
