---
title: Интерфейс IApplicationDebuggerUI | Документация Майкрософт
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
ms.openlocfilehash: e3c5f9e4cabeb4fba31bb039a7cf673ca1759860
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/16/2019
ms.locfileid: "54348910"
---
# <a name="iapplicationdebuggerui-interface"></a>Интерфейс IApplicationDebuggerUI
Реализуемый отладчик интегрированной среде разработки (IDE) (в дополнение к `IApplicationDebugger`) для предоставления внешнего компонента больший контроль над пользовательский интерфейс (UI) отладчика.  
  
 Помимо методов, наследуемых от `IUnknown`, `IApplicationDebuggerUI` интерфейс предоставляет следующие методы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание:|  
|------------|-----------------|  
|[IApplicationDebuggerUI::BringDocumentToTop](../../winscript/reference/iapplicationdebuggerui-bringdocumenttotop.md)|Открывает окно, содержащее документ указанный отладки отладчик в верхнюю часть пользовательского интерфейса.|  
|[IApplicationDebuggerUI::BringDocumentContextToTop](../../winscript/reference/iapplicationdebuggerui-bringdocumentcontexttotop.md)|Предоставляет окно, содержащее контекст заданного документа в верхнюю часть пользовательского интерфейса отладчика и прокрутка окна к контексту.|