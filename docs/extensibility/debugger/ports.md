---
title: Порты | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- ports
- debugging [Debugging SDK], ports
ms.assetid: 1d7f3aa7-7eff-4cab-bc53-0a566b1a9363
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a350e0579f7e60d8a7ffc3e879d79364cfdf0317
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31099448"
---
# <a name="ports"></a>Порты
С точки зрения архитектуры отладчик **порт**:  
  
-   Контейнер для процессов, выполняющемся на сервере. Например порт может представлять соединение на устройстве под управлением Windows CE с помощью последовательного кабеля или компьютер сети без DCOM. Один особый порт, локальный порт, содержит все процессы, запущенные на локальном компьютере.  
  
-   Могут идентифицироваться по имени или идентификатора.  
  
-   Можно перечислить все процессы, запущенные на порт и запуска и завершения этих процессов.  
  
-   Представленный [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) интерфейс, который создается путем передачи [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) аргумент [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md).  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] предоставляет порт по умолчанию, который обрабатывает все на основе Windows процессы, машинного и управляемого. Другой номер порта должен быть реализован для подключений с внешнего устройства, не под управлением Windows. Для предоставления таких Настраиваемые порты, supplier нестандартного порта также необходимо реализовать.  
  
## <a name="see-also"></a>См. также  
 [Серверы](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [Процессы](../../extensibility/debugger/processes.md)   
 [Основные понятия отладчика](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)   
 [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)