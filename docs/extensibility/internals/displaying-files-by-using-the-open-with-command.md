---
title: Отображение файлов с помощью открытого с командой (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, supporting Open With command
- Open With command
- persistence, supporting Open With command
ms.assetid: 53794bc3-1b73-4d40-954e-cfade1abddcf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4051793077e613981e1dd5b44f1736878f5853e9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708578"
---
# <a name="display-files-by-using-the-open-with-command"></a>Отображение файлов с помощью команды Open With
Проект может попросить IDE отобразить **окно Open With** Dialog. Этот запрос побуждает пользователя открыть файл с выбором стандартных редакторов. Следующие шаги описывают этот процесс:

1. Проект вызывает, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>указывая значение `OSE_UseOpenWithDialog` для `OSEOpenDocEditor` параметра.

2. На основе расширения имени файла документа IDE определяет, какие редакторы, перечисленные в реестре, могут открыть указанный документ, и отображает эту информацию в поле **Open With** dialog.

    > [!NOTE]
    > Проекты, которые имеют внутренний редактор, который должен быть включен в **Open With** диалоговые окна должны зарегистрировать фабрику редактора для каждого такого редактора. Внутренние редакторы функционируют только вместе с определенным типом проекта, который применяется при реализации метода. <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> IDE имеет встроенную фабрику редакторов для основного текстового редактора и двоичного редактора. IDE также создает экземпляр фабрики редакторов от имени каждой зарегистрированной ассоциации файлов Windows. Примером такого файла является Microsoft Word.

3. Как только пользователь выбирает элемент из **окна Open With** dialog, IDE открывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> документ методом вызова. Для получения дополнительной [How to: Open standard editors](../../extensibility/how-to-open-standard-editors.md)информации см.

## <a name="see-also"></a>См. также
- [Откройте и сохраните элементы проекта](../../extensibility/internals/opening-and-saving-project-items.md)
- [Отображение файлов с помощью команды Open File](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)
- [Как: Открытые стандартные редакторы](../../extensibility/how-to-open-standard-editors.md)
