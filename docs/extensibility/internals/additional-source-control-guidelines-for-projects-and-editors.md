---
title: "Правила управления дополнительные исходные проекты и редакторы | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control [Visual Studio SDK], guidelines for projects and editors
ms.assetid: 2483cce5-321c-4d3c-9c5c-ee8385263f74
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: ee74f16c90dbf697732a490f895efb1a52233d80
ms.lasthandoff: 02/22/2017

---
# <a name="additional-source-control-guidelines-for-projects-and-editors"></a>Правила управления дополнительные исходные проекты и редакторы
Существует ряд рекомендаций, редакторы и проекты должны соблюдаться для поддержки системы управления версиями.  
  
## <a name="guidelines"></a>Рекомендации  
 Проект или редактор должен выполнять следующие для поддержки системы управления версиями:  
  
|Область|Проект|Редактор|Подробные сведения|  
|----------|-------------|------------|-------------|  
|Частные копии файлов|x||Среда поддерживает закрытых копий файлов. То есть свой собственный частную копию файлов в этом проекте у каждого пользователя, в проект.|  
|Сохраняемость ANSI в Юникод|x|x|При написании кода сохранения состояния, сохранения файлов в формате ANSI, так как большинство программ системы управления версиями в настоящее время не поддерживают Юникод.|  
|Перечисление файлов|x||Проект должен содержать перечень всех файлов в этом и должен иметь возможность получить список файлов с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>или <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>(VSH_PROPID_First_Child или Next_Sibling).</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> Проект также должен предоставлять имена элементов с помощью его <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetMkDocument%2A>реализации и поддержке поиск имени (в том числе файлов со специальным) через его <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A>реализацию.</xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetMkDocument%2A>|  
|Текстовый формат|x|x|Если это возможно, файлы должны быть в формате для поддержки объединение различных версий. Файлы, которые не находятся в текстовом формате нельзя объединять с другими версиями файла позже. Предпочтительный текстовый формат — XML.|  
|Основано на ссылке|x||Проекты, основанные на ссылку легко поддерживаются в системе управления версиями. Однако проектов на основе каталогов поддерживаются системой управления версиями до тех пор, пока проект можно создать список его файлы по требованию, независимо от того, существуют ли эти файлы на диске. При открытии проекта из системы управления версиями, файл проекта переносится раньше любого из его файлов.|  
|Сохранять объекты и свойства в определенном порядке|x|x|Сохранять файлы в определенном порядке, например в алфавитном порядке, чтобы упростить объединение.|  
|Перезагрузить|x|x|При изменении файла на диске, редактора, необходимо перезагрузить его. Когда вы участвуете в системе управления версиями, среды перезагрузить данные можно, вызвав вашей <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A>реализацию.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> Наиболее сложная перезагрузить случаем является извлечения вызова IVsQueryEditQuerySave::<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> и обрабатываются сведения.</xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> Однако перезагрузка код должен быть возможность работать в этой ситуации.<br /><br /> Среда автоматически перезагружать файлы проекта. Тем не менее, необходимо реализовать проект <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2>Если оно содержит вложенные иерархии для поддержки перезагрузки вложенные файлы проекта.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2>|  
  
## <a name="see-also"></a>См. также  
 [Поддержка системы управления версиями](../../extensibility/internals/supporting-source-control.md)
