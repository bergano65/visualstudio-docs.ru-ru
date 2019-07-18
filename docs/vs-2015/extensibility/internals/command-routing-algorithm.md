---
title: Алгоритм маршрутизации команд | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, routing
- command routing
ms.assetid: 998b616b-bd08-45cb-845f-808efb8c33bc
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e3b8602df40045a3f4e1fc91fee92151bf5dd4ea
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68195115"
---
# <a name="command-routing-algorithm"></a>Алгоритм маршрутизации команд
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

В Visual Studio команды обрабатываются ряд различных компонентов. Команды направляются из внутреннего контекста, который основывается на текущую выборку, самый внешний контекст (также известный как глобальные). Дополнительные сведения см. в разделе [доступности](../../extensibility/internals/command-availability.md).  
  
## <a name="order-of-command-resolution"></a>Порядок выполнения команды  
 Команды передаются через следующие уровни контекст команды:  
  
1. Надстройки. Во-первых, в среде предлагает команду, чтобы надстройки, которые присутствуют.  
  
2. Приоритет команды: Эти команды регистрируются с помощью метода <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterPriorityCommandTarget>. Они вызываются для каждой команды в Visual Studio и вызываются в порядке, в котором они были зарегистрированы.  
  
3. Команды контекстного меню: Сначала находятся в контекстном меню команду предлагается в целевой объект команды, указанный в контекстное меню, а после этого для типичных маршрутизации.  
  
4. Панели инструментов задайте целевые объекты команд: Эти целевые объекты команд регистрируются при вызове <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell4.SetupToolbar2%2A>. `pCmdTarget` Параметр может быть `null`. Если это не `null`, а затем этот целевой объект команды используется для обновления любых команд на панели инструментов, вы настраиваете. Если оболочка — Настройка панели инструментов, то он передает рамка окна, в качестве `pCmdTarget` таким образом, чтобы все обновления для команды на панели инструментов последовательности через рамку окна, даже если он недопустим в фокусе.  
  
5. Окно инструментов: Средство windows, которые обычно реализуют <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> интерфейс, необходимо также реализовать <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейса таким образом, Visual Studio можно получить целевой объект команды, когда окно инструментов является активным окном. Тем не менее, если окно инструментов, который имеет фокус находится **проекта** окна, то команда отправляется <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> интерфейс, который является общий родительский объект для выбранных элементов. Если этот выбор распространяется на несколько проектов, команда отправляется <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution> иерархии. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> Интерфейс содержит <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> методы, которые аналогичны соответствующих команд на <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейс.  
  
6. Окно документа: Если команда имеет флаг RouteToDocs в его vsct-файл, Visual Studio выполняет поиск целевого объекта команды в объекте представления документа, равное либо экземпляр <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> интерфейс или экземпляра объекта документа (обычно <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> интерфейс или <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> интерфейс). Если в объекте представления документа не поддерживает команды, Visual Studio направляет команду, чтобы <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейс, который возвращается. (Это необязательный интерфейс для объектов данных документа).  
  
7. Текущей иерархии: Текущей иерархии может быть проект, который является владельцем активного окна документа или иерархии, который выбран в **обозревателе решений**. Visual Studio ищет <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейс, реализуемый в текущей или активных иерархии. Команды, которые являются допустимыми, каждый раз, когда иерархии активен, даже если фокус находится в окне документа элемент проекта должен поддерживать иерархия. Однако команды, которые применяются только тогда, когда **обозревателе решений** имеет фокус должен поддерживаться с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> интерфейса и его <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>методы.  
  
     **Вырезать**, **копирования**, **вставить**, **удалить**, **Переименовать**, **введите**и **DoubleClick** команды требуют специальной обработки. Сведения о том, как обрабатывать **удалить** и **удалить** команды в иерархии, см. в разделе <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler> интерфейс.  
  
8. Глобальные: Если команда не было обработано, упомянутых ранее контекстах, Visual Studio пытается направить ее VSPackage, которому принадлежит команду, которая реализует <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейс. Если VSPackage уже не был загружен, он не загружается при Visual Studio вызывает <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> метод. Только тогда, когда загружается VSPackage <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> вызывается метод.  
  
## <a name="see-also"></a>См. также  
 [Конструктор команд](../../extensibility/internals/command-design.md)
