---
title: Алгоритм маршрутизации команд | Документация Майкрософт
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
- commands, routing
- command routing
ms.assetid: 998b616b-bd08-45cb-845f-808efb8c33bc
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2136bbff40a24b1b376d5d737367630256230c35
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47573274"
---
# <a name="command-routing-algorithm"></a>Алгоритм маршрутизации команд
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [алгоритм маршрутизации команд](https://docs.microsoft.com/visualstudio/extensibility/internals/command-routing-algorithm).  
  
В Visual Studio команды обрабатываются ряд различных компонентов. Команды направляются из внутреннего контекста, который основывается на текущую выборку, самый внешний контекст (также известный как глобальные). Дополнительные сведения см. в разделе [доступности](../../extensibility/internals/command-availability.md).  
  
## <a name="order-of-command-resolution"></a>Порядок выполнения команды  
 Команды передаются через следующие уровни контекст команды:  
  
1.  Надстроек: Во-первых среде предлагает команду, чтобы надстройки, которые присутствуют.  
  
2.  Приоритет команды: эти команды регистрируются с помощью метода <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterPriorityCommandTarget>. Они вызываются для каждой команды в Visual Studio и вызываются в порядке, в котором они были зарегистрированы.  
  
3.  Команды контекстного меню: сначала находятся в контекстном меню команду предлагается в целевой объект команды, указанный в контекстное меню, а после этого для типичных маршрутизации.  
  
4.  Набор целей команды панелей инструментов: эти целевые объекты команд регистрируются при вызове <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell4.SetupToolbar2%2A>. `pCmdTarget` Параметр может быть `null`. Если это не `null`, а затем этот целевой объект команды используется для обновления любых команд на панели инструментов, вы настраиваете. Если оболочка — Настройка панели инструментов, то он передает рамка окна, в качестве `pCmdTarget` таким образом, чтобы все обновления для команды на панели инструментов последовательности через рамку окна, даже если он недопустим в фокусе.  
  
5.  Окно инструментов: Средство windows, которые обычно реализуют <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> интерфейс, необходимо также реализовать <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейса таким образом, Visual Studio можно получить целевой объект команды, когда окно инструментов является активным окном. Тем не менее, если окно инструментов, который имеет фокус находится **проекта** окна, то команда отправляется <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> интерфейс, который является общий родительский объект для выбранных элементов. Если этот выбор распространяется на несколько проектов, команда отправляется <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution> иерархии. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> Интерфейс содержит <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> методы, которые аналогичны соответствующих команд на <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейс.  
  
6.  Окно документа: Если команда имеет флаг RouteToDocs в его vsct-файл, Visual Studio выполняет поиск целевого объекта команды в объекте представления документа, равное либо экземпляр <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> интерфейс или экземпляра объекта документа (обычно <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>интерфейс или <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> интерфейс). Если в объекте представления документа не поддерживает команды, Visual Studio направляет команду, чтобы <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейс, который возвращается. (Это необязательный интерфейс для объектов данных документа).  
  
7.  Текущей иерархии: текущей иерархии может быть проект, который является владельцем активного окна документа или иерархии, который выбран в **обозревателе решений**. Visual Studio ищет <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейс, реализуемый в текущей или активных иерархии. Команды, которые являются допустимыми, каждый раз, когда иерархии активен, даже если фокус находится в окне документа элемент проекта должен поддерживать иерархия. Однако команды, которые применяются только тогда, когда **обозревателе решений** имеет фокус должен поддерживаться с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> интерфейса и его <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>методы.  
  
     **Вырезать**, **копирования**, **вставить**, **удалить**, **Переименовать**, **введите**и **DoubleClick** команды требуют специальной обработки. Сведения о том, как обрабатывать **удалить** и **удалить** команды в иерархии, см. в разделе <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler> интерфейс.  
  
8.  Global: Если команда не было обработано, упомянутых ранее контекстах, Visual Studio пытается направить ее VSPackage, которому принадлежит команду, которая реализует <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейс. Если VSPackage уже не был загружен, он не загружается при Visual Studio вызывает <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> метод. Только тогда, когда загружается VSPackage <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> вызывается метод.  
  
## <a name="see-also"></a>См. также  
 [Конструктор команд](../../extensibility/internals/command-design.md)

