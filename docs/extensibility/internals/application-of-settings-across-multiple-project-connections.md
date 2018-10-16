---
title: Применение параметров в нескольких подключениях проекта | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, application of settings
ms.assetid: 2116d3d0-c46c-4d0a-b482-08a178584f46
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6d8b8d7d6dc1e596686a2fad7b53363b2387a47b
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/03/2018
ms.locfileid: "39500047"
---
# <a name="application-of-settings-across-multiple-project-connections"></a>Применение параметров в нескольких подключениях проекта
Подключаемый модуль системы управления версиями созданные с помощью источника управления Plug-in API версии 1.2, можно использовать пакетную операцию выполнения же операция системы управления версиями для нескольких проектов или несколько контекстов соединений. Чтобы устранить избыточную, диалоговые окна в интерфейсе пользователя для каждого проекта можно использовать пакеты.  
  
 Если пользователь выбирает несколько элементов, принадлежащих одновременно несколько соединений в подключаемый модуль системы управления версиями, созданные с помощью источника управления Plug-in API с версии 1.1 (например, два веб-проектов на компьютерах разных общую папку) и проверяет их, пользователь видит же диалоговое окно повторно. Это происходит, даже если пользователь нажимает кнопку **применить ко всем** флажок в диалоговом окне, так как в интегрированной среде разработки сбрасывает свое состояние для каждого контекста соединения.  
  
## <a name="new-capability-flag"></a>Новые возможности флаг  
 `SccBeginBatch` Функции наборов `SCC_CAP_BATCH` флаг, указывающий, что пакетная операция выполняется.  
  
## <a name="new-functions"></a>Новые функции  
Следующие новые функции поддерживают пакетной операции.  
  
-   [SccBeginBatch](../../extensibility/sccbeginbatch-function.md)  
  
-   [SccEndBatch](../../extensibility/sccendbatch-function.md)  

  
`SCCBeginBatch` Начинается с функции группы операций системы управления версиями. `SccEndBatch` Функция закрывает группе. Группы не могут быть вложенными.  
  
## <a name="see-also"></a>См. также  
 [Новые возможности в исходный элемент управления Plug-in API версии 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)