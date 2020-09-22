---
title: Доступность команды | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, context
- menu items, visibility contexts
ms.assetid: c74e3ccf-d771-48c8-a2f9-df323b166784
caps.latest.revision: 35
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f060f6c49fc02c75b3fe9f792133c9ee88c6d56c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842384"
---
# <a name="command-availability"></a>Доступность команд
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Контекст Visual Studio определяет доступные команды. Контекст может изменяться в зависимости от текущего проекта, текущего редактора, загруженных пакетов VSPackage и других аспектов интегрированной среды разработки (IDE).  
  
## <a name="command-contexts"></a>Контексты команд  
 Наиболее распространены следующие контексты команд.  
  
- **Интегрированная среда разработки** Команды, предоставляемые интегрированной средой разработки, доступны всегда.  
  
- Пакет **VSPackage** Пакеты VSPackage могут определять, когда следует отображать или скрывать команды.  
  
- **Проект Project** Команды проекта отображаются только для текущего выбранного проекта.  
  
- **Редактор** В каждый момент времени активным может быть только один редактор. Доступны команды из активного редактора. Редактор тесно работает с языковой службой. Языковая служба должна обработать свои команды в контексте связанного редактора.  
  
- **Тип файла** Редактор может загружать более одного типа файлов. Доступные команды могут изменяться в зависимости от типа файла.  
  
- **Активное окно** В последнем активном окне документа задается контекст пользовательского интерфейса для привязок к ключам. Однако окно инструментов с таблицей привязки к ключам, похожее на внутренний веб-браузер, может также установить контекст пользовательского интерфейса. Для окон документов с несколькими вкладками, таких как редактор HTML, каждая вкладка имеет свой идентификатор GUID контекста команды. После регистрации окно инструментов всегда доступно в меню **вид** .  
  
- **Контекст пользовательского интерфейса** Контексты пользовательского интерфейса определяются значениями <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT> класса, например <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionBuilding_guid> при сборке решения или <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Debugging_guid> при активном отладчике. Несколько контекстов пользовательского интерфейса могут быть активными одновременно.  
  
## <a name="defining-custom-context-guids"></a>Определение пользовательских идентификаторов GUID контекста  
 Если соответствующий идентификатор GUID контекста команды еще не определен, можно определить его в VSPackage, а затем запрограммировать его как активный или неактивный, чтобы управлять видимостью команд.  
  
1. Зарегистрируйте идентификаторы GUID контекста, вызвав <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> метод.  
  
2. Получите состояние GUID контекста, вызвав <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> метод.  
  
3. Включите или отключите контекстные GUID контекста, вызвав <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> метод.  
  
    > [!CAUTION]
    > Убедитесь, что VSPackage не влияет на существующие идентификаторы GUID контекста, так как от них могут зависеть другие пакеты VSPackage.  
  
## <a name="see-also"></a>См. также:  
 [Объекты контекста выделения](../../extensibility/internals/selection-context-objects.md)   
 [Как добавить элементы пользовательского интерфейса с помощью пакетов VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
