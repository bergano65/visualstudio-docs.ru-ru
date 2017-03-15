---
title: "Проект контекста | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: d1803f4a-24eb-44b0-b5d2-cb40c15534be
caps.latest.revision: 10
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
ms.openlocfilehash: d74d804f65338edb589e63dde111e2ec1a4b5c6f
ms.lasthandoff: 02/22/2017

---
# <a name="project-context"></a>Контекст проекта
Когда пользователь добавляет или работает с проектов и элементов проектов, интегрированной среды разработки использует концепцию контекста проекта, чтобы определить, как различные операции должны выполняться.  
  
 Как правило, файлы являются объектами стандартного проекта, которые пользователь явно создается путем выбора **новый проект** команды или делает доступным, выбрав **открыть проект** на **файл** меню. В этих случаях файлы создаются и открыт в контексте проекта и тип проекта определяет контекст для редактирования документа.  
  
 Некоторые проекты предоставляют богатый контекста. Например проект управляет имен уровня проекта, программный или подключения базы данных уровня проекта для привязки данных. Пользователь может часто открытых файлов или подключения к базе данных непосредственно с помощью объекта конкретного проекта, такие как элемент проекта отобразится в обозревателе решений.  
  
 В других случаях контекст проекта элемента не указано явным образом. Например, контекст элемента недоступен при открытии файла, выбрав **откройте существующий файл** на **файл** меню, когда отладчик работает с файлом или когда пользователь щелкает **поиска в файлах** в **поиск и замена** диалоговое окно. Обрабатывать эти ситуации IDE вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument>для управления процессом поиска лучший проект, чтобы открыть документ.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument>  
  
## <a name="see-also"></a>См. также  
 [Приоритет проекта](../../extensibility/internals/project-priority.md)   
 [Добавление проекта и шаблоны элементов проекта](../../extensibility/internals/adding-project-and-project-item-templates.md)
