---
title: Применение параметров в нескольких подключениях проекта | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control plug-ins, application of settings
ms.assetid: 2116d3d0-c46c-4d0a-b482-08a178584f46
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 81d6a1f540314863e4e24b3b91c7f4112e0af8f0
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49197617"
---
# <a name="application-of-settings-across-multiple-project-connections"></a>Применение параметров в нескольких подключениях проекта
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Подключаемый модуль системы управления версиями соблюдались 1.2 API подключаемого модуля управления источника, можно использовать пакетную операцию выполнения же операция системы управления версиями для нескольких проектов или несколько контекстов соединений. Чтобы устранить избыточную, диалоговые окна в интерфейсе пользователя для каждого проекта можно использовать пакеты.  
  
 Если пользователь выбирает несколько элементов, принадлежащих одновременно несколько соединений в подключаемый модуль системы управления версиями, созданные с помощью подключаемого модуля API источника управления 1.1, (например, два веб-проектов на компьютерах разных общую папку) и проверяет их, пользователь увидит же диалоговое окно несколько раз. Это происходит, даже если пользователь нажимает кнопку **применить ко всем** флажок в диалоговом окне, так как в интегрированной среде разработки сбрасывает свое состояние для каждого контекста соединения.  
  
## <a name="new-capability-flag"></a>Новые возможности флаг  
 `SccBeginBatch` Функции наборов `SCC_CAP_BATCH` флаг, указывающий, что пакетная операция выполняется  
  
## <a name="new-functions"></a>Новые функции  
 Следующие новые функции поддерживают пакетной операции.  
  
-   [SccBeginBatch](../../extensibility/sccbeginbatch-function.md)  
  
-   [SccEndBatch](../../extensibility/sccendbatch-function.md)  
  
 `SCCBeginBatch` Начинается с функции группы операций системы управления версиями. `SccEndBatch` Закрывает группе. Группы не могут быть вложенными.  
  
## <a name="see-also"></a>См. также  
 [Новые возможности в API версии 1.2 подключаемого модуля системы управления версиями](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)

