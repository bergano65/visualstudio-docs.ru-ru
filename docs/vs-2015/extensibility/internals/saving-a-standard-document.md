---
title: Сохранение стандартного документа | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], saving standard documents
- projects [Visual Studio SDK], saving standard documents
- persistence, saving standard documents
ms.assetid: d692fedf-b46e-4d60-84bd-578635042235
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5040070287db6486fa62c9010fe023be31b04cbe
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198089"
---
# <a name="saving-a-standard-document"></a>Сохранение стандартного документа
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Среда обрабатывает команды Сохранить, сохранить как и сохранить все. Когда пользователь выбирает команду **сохранить**, **Сохранить как**или **сохранить все** из меню **файл** или закрывает **решение, в**результате чего выполняется следующий процесс.  
  
 ![Standard Edition](../../extensibility/internals/media/public.gif "Общие")  
Сохранение, сохранение как и сохранение всей обработки команд для стандартного редактора  
  
 Этот процесс описан в следующих шагах.  
  
1. Если выбраны команды **сохранить** и **Сохранить как** , среда использует <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> службу для определения активного окна документа и, таким образом, элементы, которые следует сохранить. Когда окно активного документа будет известно, среда находит указатель иерархии и идентификатор элемента (itemID) для документа в выполняемой таблице документов. Дополнительные сведения см. в разделе [выполнение таблицы документов](../../extensibility/internals/running-document-table.md).  
  
    Если выбрана команда **сохранить все** , среда использует сведения из таблицы «выполняемый документ» для компиляции списка всех элементов для сохранения.  
  
2. Когда решение получает <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> вызов, оно проходит по набору выбранных элементов (то есть множественный выбор, предоставляемый <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> службой).  
  
3. В каждом выбранном элементе решение использует указатель иерархии для вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> метода, чтобы определить, должна ли быть включена команда меню " **сохранить** ". Если один или несколько элементов являются "грязными", команда " **сохранить** " будет включена. Если в иерархии используется стандартный редактор, то иерархия делегирует запрос о состоянии "грязного" в редактор, вызывая <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A> метод.  
  
4. Для каждого выбранного элемента, который является "грязным", решение использует указатель иерархии для вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> метода в соответствующих иерархиях.  
  
    Обычно в иерархии для редактирования документа используется стандартный редактор. В этом случае объект данных документа для этого редактора должен поддерживать <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> интерфейс. После получения <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> вызова метода проект должен сообщить редактору, что документ сохраняется, вызвав <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.SaveDocData%2A> метод для объекта данных документа. Редактор может разрешить среде обработку диалогового окна " **Сохранить как** ", вызвав `Query Service` <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> интерфейс. Он возвращает указатель на <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> интерфейс. Затем редактор должен вызвать <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A> метод, передав указатель на <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> реализацию редактора с помощью `pPersistFile` параметра. Затем среда выполняет операцию сохранения и предоставляет диалоговое окно « **Сохранить как** » для редактора. Затем среда выполняет обратный вызов к редактору с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> .  
  
5. Если пользователь пытается сохранить документ без заголовка (то есть ранее несохраненный документ), то выполняется команда Сохранить как.  
  
6. Для команды "Сохранить как" среда отображает диалоговое окно Сохранить как, предлагающее пользователю ввести имя файла.  
  
    Если имя файла изменилось, то иерархия отвечает за обновление кэшированных данных фрейма документа путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A> (VSFPROPID_MkDocument).  
  
   Если команда **Сохранить как** перемещает расположение документа, а иерархия чувствительна к расположению документа, то иерархия отвечает за передачу владения открытым окном документа в другую иерархию. Например, это происходит, если проект отслеживает, является ли файл внутренним или внешним файлом (прочим файлом) относительно проекта. Используйте следующую процедуру, чтобы изменить принадлежность файла к проекту прочих файлов.  
  
## <a name="changing-file-ownership"></a>Изменение владельца файла  
  
#### <a name="to-change-file-ownership-to-the-miscellaneous-files-project"></a>Изменение владельца файла на проект прочих файлов  
  
1. Служба запросов для <xref:Microsoft.VisualStudio.Shell.Interop.SVsExternalFilesManager> интерфейса.  
  
     Возвращается указатель на <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2> .  
  
2. Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2.TransferDocument%2A> `pszMkDocumentNew` метод (, `punkWindowFrame` ), чтобы переместить документ в новую иерархию. Иерархия, выполняющая команду "Сохранить как", вызывает этот метод.  
  
## <a name="see-also"></a>См. также:  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [Открытие и сохранение элементов проекта](../../extensibility/internals/opening-and-saving-project-items.md)
