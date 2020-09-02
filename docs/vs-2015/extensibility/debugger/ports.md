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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153687"
---
# <a name="ports"></a>Порты
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

В плане архитектуры отладчика **порт**:  
  
- — Это контейнер для набора процессов, выполняющихся на сервере. Например, порт может представлять подключение к Windows CE устройству по последовательному кабелю или сетевому компьютеру, не являющемуся DCOM. Один специальный порт, называемый локальным портом, содержит все процессы, запущенные на локальном компьютере.  
  
- Может идентифицировать себя по имени или идентификатору.  
  
- Может перечислить все процессы, запущенные в порте, и запустить и завершить эти процессы.  
  
- Представляется интерфейсом [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) , который создается путем передачи аргумента [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) в [аддпорт](../../extensibility/debugger/reference/idebugportsupplier2-addport.md).  
  
  [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] предоставляет порт по умолчанию, который обрабатывает все процессы на основе Windows, а именно — в машинном и управляемом. Пользовательский порт должен быть реализован для соединений с внешними устройствами, не основанными на Windows. Для предоставления таких пользовательских портов необходимо также реализовать пользовательский поставщик порта.  
  
## <a name="see-also"></a>См. также:  
 [Серверах](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [Операций](../../extensibility/debugger/processes.md)   
 [Основные понятия отладчика](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)   
 [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
