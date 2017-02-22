---
title: "Порты | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "порты"
  - "отладка [пакет SDK для отладки], порты"
ms.assetid: 1d7f3aa7-7eff-4cab-bc53-0a566b1a9363
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# Порты
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

В терминах архитектуры отладчика, a **Порт**.  
  
-   Контейнер для набора процессов, выполняющихся на сервере.  Например, порт может представлять подключения к устройству CE\-основанному окнами серийного хвостом или в сетевых компьютер non\-DCOM.  Один специальный локальный порт с именем порта, содержащую всех процессов, запущенных на локальном компьютере.  
  
-   Можно указать по имени или идентификатору.  
  
-   Может перечислить все процессы запуска на порту и запустить и завершить эти процессы.  
  
-   Представляет  [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) интерфейс, который создается путем передачи  [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) аргумент  [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md).  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] предоставляет по умолчанию порт, который обрабатывает все процессы Windows, собственный и управляемый код.  Нестандартный порт должен быть реализован для соединений с внешними механизмами, не на базе Windows.  Чтобы предоставить такие пользовательские порты, настраиваемому поставщику порта также требуется реализовывать.  
  
## См. также  
 [Серверы](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [Процессы](../../extensibility/debugger/processes.md)   
 [Основные понятия отладчика](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)   
 [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)