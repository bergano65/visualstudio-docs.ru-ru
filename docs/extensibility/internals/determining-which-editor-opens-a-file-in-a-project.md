---
title: Определение того, какой редактор открывает файл в проекте (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], determining which editor opens a file
- projects [Visual Studio SDK], determining which editor opens file
- project types, determining which editor opens a file
- persistence, determining which editor opens a file
ms.assetid: acbcf4d8-a53a-4727-9043-696a47369479
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: af7037a3b4bfbae1801e802256af240d017d2789
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708660"
---
# <a name="determine-which-editor-opens-a-file-in-a-project"></a>Определить, какой редактор открывает файл в проекте
Когда пользователь открывает файл в проекте, среда проходит через процесс опроса, в конечном итоге открывая соответствующий редактор или дизайнер для этого файла. Первоначальная процедура, используемая средой, одинакова как для стандартных, так и для пользовательских редакторов. Среда использует различные критерии при опросе, который редактор использовать для открытия файла и VSPackage должен координироваться с окружающей средой во время этого процесса.

 Например, когда пользователь выбирает **команду Open** из меню **файла,** а затем выбирает *filename.rtf* (или любой другой <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> файл с расширением *.rtf),* среда вызывает реализацию для каждого проекта, в конечном итоге езда на велосипеде через все экземпляры проекта в решении. Проекты возвращают набор флагов, которые определяют претензии к документу по приоритету. Используя наивысший приоритет, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> среда вызывает соответствующий метод. Для получения дополнительной информации о процессе голосования [см.](../../extensibility/internals/adding-project-and-project-item-templates.md)

 Проект «Разные файлы» утверждает все файлы, на которые не претендуют другие проекты. Таким образом, пользовательские редакторы могут открывать документы до того, как стандартные редакторы откроют их. Если проект «Разные файлы» требует файла, среда вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> метод для открытия файла со стандартным редактором. Среда проверяет свой внутренний список зарегистрированных редакторов для того, который обрабатывает файлы *.rtf.* Этот список находится в реестре по следующему ключу:

 **HKEY_LOCAL_MACHINE-Программное обеспечение,Microsoft-VisualStudio\\\<версия\\\<>»Редактор ы фабрика гид>**

 Среда также проверяет идентификаторы классов в ключе **HKEY_CLASSES_ROOT clSID** для любых объектов, которые имеют подключку **DocObject.** Если там найдено расширение файла, встроенная версия приложения, например Microsoft Word, создается на месте в Visual Studio. Эти объекты документа должны быть <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage> сложными файлами, <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> которые реализуют интерфейс, или объект должен реализовать интерфейс.

 Если в реестре нет фабрики редакторов для файлов *.rtf,* то среда выглядит в **ключе HKEY_CLASSES_ROOT\\.rtf** и открывает указанный там редактор. Если расширение файла не найдено в **HKEY_CLASSES_ROOT,** то среда использует основной текстовый редактор Visual Studio, чтобы открыть файл, если это текстовый файл.

 Если основной текстовый редактор выходит из строя, что происходит, если файл не является текстовым файлом, то среда использует свой двоичный редактор для файла.

 Если среда находит редактор для расширения *.rtf* в своем реестре, она загружает VSPackage, который реализует эту фабрику редакторов. Среда вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> метод на новом VSPackage. VSPackage `QueryService` `SID_SVsRegistorEditor`требует, используя <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> метод для регистрации редактора завода с окружающей средой.

 Среда теперь перепроверяет свой внутренний список зарегистрированных редакторов, чтобы найти недавно зарегистрированную фабрику редакторов для файлов *.rtf.* Среда вызывает реализацию метода, <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> передавая имя файла и тип представления для создания.

## <a name="see-also"></a>См. также
- <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>
- <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>
