---
title: Применение параметров подключения нескольких проектов | Документы Microsoft
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
ms.openlocfilehash: 0dff30ea80fb2de9bf4d90ffa48cd2f9b3d40756
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="application-of-settings-across-multiple-project-connections"></a>Применение параметров подключения нескольких проектов
Подключаемый модуль системы управления версиями созданное с помощью 1.2 API подключаемого модуля управления источника, можно использовать пакетную операцию на обработку же операция системы управления версиями в нескольких проектах или несколько контекстов соединений. Пакеты можно использовать для устранения избыточных, диалоговые окна работу пользователей на проект.  
  
 Если пользователь выбирает несколько элементов, принадлежащих больше одного соединения в подключаемый модуль системы управления версиями, созданное с помощью подключаемого модуля API источника управления 1.1, (например, два веб-проектов на компьютерах разных общую папку) и проверяет их, пользователь видит же диалоговое окно несколько раз. Это происходит, даже если пользователь нажимает кнопку **применить ко всем** флажок в диалоговом окне, так как в Интегрированной среде разработки сбрасывает свое состояние для каждого контекста соединения.  
  
## <a name="new-capability-flag"></a>Новые возможности флаг  
 `SccBeginBatch` Функции наборов `SCC_CAP_BATCH` флаг, указывающий, что пакетная операция идет  
  
## <a name="new-functions"></a>Новые функции  
 Следующие новые функции поддерживают пакетную операцию.  
  
-   [SccBeginBatch](../../extensibility/sccbeginbatch-function.md)  
  
-   [SccEndBatch](../../extensibility/sccendbatch-function.md)  
  
 `SCCBeginBatch` Начинается с функции группы операций системы управления версиями. `SccEndBatch` Закрывает группе. Группы не могут быть вложенными.  
  
## <a name="see-also"></a>См. также  
 [Новые возможности в API версии 1.2 подключаемого модуля системы управления версиями](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)