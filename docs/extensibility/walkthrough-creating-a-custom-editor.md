---
title: 'Прохождение: Создание пользовательского редактора Документы Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - create
ms.assetid: d090abb6-d99f-4083-a3db-cd16bf81ce7d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7eb376637fd72f3856415ee2527ec622fea02950
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697665"
---
# <a name="walkthrough-create-a-custom-editor"></a>Прохождение: Создание пользовательского редактора
Шаблон проекта VSPackage может создать простой пользовательский редактор в СЗ. Шаблон проекта VSPackage больше не поддерживает проекты «Си» или «Визуальные основы». Для получения дополнительной информации, [см.](../extensibility/visual-studio-sdk.md)

## <a name="prerequisites"></a>Предварительные требования
 Для выполнения этого пошагового руководства необходимо установить пакет SDK для Visual Studio. Для получения дополнительной информации, [см.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="the-visual-studio-package-project-template"></a>Шаблон проекта Visual Studio Package
 Шаблон проекта Visual Studio Package можно найти в диалоге **нового проекта** под папкой **«Расширяемые** возможности».

### <a name="to-create-a-vspackage-using-the-visual-studio-package-template"></a>Создание VSPackage с помощью шаблона пакета Visual Studio

1. Создайте проект с шаблоном Visual Studio Package.

2. Выберите опцию **пользовательский редактор** и нажмите **далее**. Отображается страница **Параметры редактора.**

3. Введите имя редактора в поле **имени редактора.** Введите расширение файла, которое вы хотите быть связано с редактором в поле **расширения файла.** Ваш редактор доступен для файлов с этим расширением. Расширение файла зарегистрировано только для Visual Studio, а не для Windows. Введите имя файла по умолчанию для новых документов, созданных с редактором в поле **имя файла по умолчанию.**

4. Нажмите кнопку **Готово** , чтобы создать VSPackage в указанной папке.

### <a name="to-test-your-custom-editor"></a>Чтобы проверить пользовательский редактор

1. В меню **файла,** укажите на **новый,** а затем нажмите **файл**.

2. В **панели установленных шаблонов** в диалоговом поле **Нового Файла** выберите шаблон файла, а затем тип файла, который вы зарегистрировали.

3. Нажмите **Открыть** для просмотра и отоденать документ.

     Редактор поддерживает операции вырезания и вставки, поиска и замены и операции с открытой нагрузкой.

## <a name="see-also"></a>См. также
- [Пакеты VSPackage](../extensibility/internals/vspackages.md)
