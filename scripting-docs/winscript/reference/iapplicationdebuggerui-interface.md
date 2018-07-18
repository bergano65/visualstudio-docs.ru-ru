---
title: Интерфейс IApplicationDebuggerUI | Документы Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: dbaa04f6790ffc4d80447a6745ca82cc8dba6802
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24725144"
---
# <a name="iapplicationdebuggerui-interface"></a>Интерфейс IApplicationDebuggerUI
Реализуемый отладчик интегрированной среды разработки (IDE) (в дополнение к `IApplicationDebugger`) для предоставления больший контроль над пользовательского интерфейса (UI) отладчик внешнего компонента.  
  
 Помимо методов, наследуемых от `IUnknown`, `IApplicationDebuggerUI` интерфейс предоставляет следующие методы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|------------|-----------------|  
|[IApplicationDebuggerUI::BringDocumentToTop](../../winscript/reference/iapplicationdebuggerui-bringdocumenttotop.md)|Переводит окно, содержащее документ указанный отладки отладчик в верхнюю часть пользовательского интерфейса.|  
|[IApplicationDebuggerUI::BringDocumentContextToTop](../../winscript/reference/iapplicationdebuggerui-bringdocumentcontexttotop.md)|Переводит окно, содержащее контекст данного документа в верхнюю часть пользовательского интерфейса отладчика и Прокручивает окно до контекста.|