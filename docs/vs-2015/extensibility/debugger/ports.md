---
title: Порты | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- ports
- debugging [Debugging SDK], ports
ms.assetid: 1d7f3aa7-7eff-4cab-bc53-0a566b1a9363
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 73003e00fef5c37db4a702e7a4a1121600673844
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58979799"
---
# <a name="ports"></a>Порты
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

С точки зрения архитектуры отладчика **порт**:  
  
- Контейнер для набора процессов выполняется на сервере. Например порт может представлять связь на основе Windows CE устройство с помощью последовательного кабеля или на компьютер сети без DCOM. Один особый порт, локальный порт, содержит все процессы, запущенные на локальном компьютере.  
  
- Можно идентифицировать себя по имени или идентификатора.  
  
- Можно перечислить все процессы, запущенные на порт и запуска и завершения этих процессов.  
  
- Представленный [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) интерфейс, который создается путем передачи [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) аргумент [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md).  
  
  [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] предоставляет порт по умолчанию, который обрабатывает все на базе Windows процессы, машинного и управляемого кода. Другой номер порта должен быть реализован для соединения с внешними устройствами, которые не основаны на Windows. Чтобы предоставить такие настраиваемые порты, поставщика пользовательского порта также должна быть реализована.  
  
## <a name="see-also"></a>См. также  
 [Серверы](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [Процессы](../../extensibility/debugger/processes.md)   
 [Отладчик: основные понятия](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)   
 [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
