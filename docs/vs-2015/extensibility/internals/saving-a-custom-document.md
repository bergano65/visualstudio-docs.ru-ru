---
title: Сохранение настраиваемого документа | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- persistence, saving custom documents
- projects [Visual Studio SDK], saving custom documents
- editors [Visual Studio SDK], saving custom documents
ms.assetid: 040b36d6-1f0a-4579-971c-40fbb46ade1d
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d5a25cc7f64c50ca088e11cc69a122f97333dfc3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47568665"
---
# <a name="saving-a-custom-document"></a>Сохранение настраиваемого документа
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [сохранение a Custom Document](https://docs.microsoft.com/visualstudio/extensibility/internals/saving-a-custom-document).  
  
Дескрипторы среды **Сохранить**, **Сохранить как**, и **сохранить все** команды. Когда пользователь щелкает **Сохранить**, **Сохранить как**, **или сохранить все** на **файл** меню или закрывает решение, приводит к Save All, следующие процесс выполняется.  
  
 ![Сохранение редактора клиента](../../extensibility/internals/media/private.gif "закрытый")  
Сохранить, сохранить как и сохранить все обработки команд для пользовательского редактора  
  
 Этот процесс подробно описан в следующих шагах:  
  
1.  Для **Сохранить** и **Сохранить как** команды, в среде используется <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> службы для определения активного окна документа, и таким образом следует сохранить какие элементы. После получения активном окне документа среды находит указатель иерархии и идентификатор элемента (itemID) для документа в таблице выполняющихся документов. Дополнительные сведения см. в разделе [таблице выполняющихся документов](../../extensibility/internals/running-document-table.md).  
  
     Сохранить все команды в среде используется для компиляции список всех элементов, чтобы сохранить данные в таблице выполняющихся документов.  
  
2.  При получении решение <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> вызова, он проходит по коллекции набор выбранных элементов (то есть множественного выбора, предоставляемыми <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> службы).  
  
3.  Для каждого элемента в выделении, решение использует указатель иерархии для вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> метод, чтобы определить, включены ли команды меню «Сохранить». Если один или несколько элементов "грязные", команды "Сохранить" включен. Если в иерархии используется стандартный редактор, затем делегаты иерархии, запрашивая "грязных" состояние в редактор, вызвав <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A> метод.  
  
4.  Для каждого выбранного элемента, который является "грязным", решение использует указатель иерархии для вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> метод соответствующие иерархий.  
  
     В случае пользовательского редактора обмен данными между объектом данных документа и проект является закрытым. Таким образом любые вопросы специальные сохраняемости обрабатываются между этими двумя объектами.  
  
    > [!NOTE]
    >  Если вы реализуете собственный сохраняемости, необходимо вызвать <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> способ сэкономить время. Этот метод проверяет, чтобы убедиться в том, что он безопасен для сохранения файла (например, файл не только для чтения).  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [Открытие и сохранение элементов проекта](../../extensibility/internals/opening-and-saving-project-items.md)

