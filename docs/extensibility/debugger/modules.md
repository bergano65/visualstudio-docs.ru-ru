---
title: Модули | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- modules
- debugging [Debugging SDK], modules
ms.assetid: c4cf2809-dbdb-4e75-9273-b3d3d77b67d0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f587e015263336436588d14edeeb5c6935872950
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="modules"></a>Модули
С точки зрения архитектуры отладчик **модуль**:  
  
-   Представляет собой Физический контейнер код, например исполняемый файл или библиотеку DLL.  
  
-   Можно перезагрузить его символы и описывать себя. Описание модуля, отображаются в окне модули интегрированной среды разработки.  
  
-   Представленный [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md) интерфейс, созданный модуль отладки для описания модуля.  
  
## <a name="see-also"></a>См. также  
 [Основные понятия отладчика](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)