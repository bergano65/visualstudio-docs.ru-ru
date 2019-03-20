---
title: Интерфейс IApplicationDebuggerUI | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IApplicationDebuggerUI interface
ms.assetid: b8828817-ca24-4012-802c-7dcaeea65dc8
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f138492e5b0a465bb0f101c15457ed1021ab3d5a
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58146188"
---
# <a name="iapplicationdebuggerui-interface"></a>Интерфейс IApplicationDebuggerUI
Реализуемый отладчик интегрированной среде разработки (IDE) (в дополнение к `IApplicationDebugger`) для предоставления внешнего компонента больший контроль над пользовательский интерфейс (UI) отладчика.  
  
 Помимо методов, наследуемых от `IUnknown`, `IApplicationDebuggerUI` интерфейс предоставляет следующие методы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|------------|-----------------|  
|[IApplicationDebuggerUI::BringDocumentToTop](../../winscript/reference/iapplicationdebuggerui-bringdocumenttotop.md)|Открывает окно, содержащее документ указанный отладки отладчик в верхнюю часть пользовательского интерфейса.|  
|[IApplicationDebuggerUI::BringDocumentContextToTop](../../winscript/reference/iapplicationdebuggerui-bringdocumentcontexttotop.md)|Предоставляет окно, содержащее контекст заданного документа в верхнюю часть пользовательского интерфейса отладчика и прокрутка окна к контексту.|