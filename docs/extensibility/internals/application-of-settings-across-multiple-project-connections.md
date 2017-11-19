---
title: "Применение параметров подключения нескольких проектов | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: source control plug-ins, application of settings
ms.assetid: 2116d3d0-c46c-4d0a-b482-08a178584f46
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9750d946a941e86a6c0a6973661f00f8f44cf9b5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="application-of-settings-across-multiple-project-connections"></a>Применение параметров подключения нескольких проектов
Подключаемый модуль системы управления версиями созданное с помощью 1.2 API подключаемого модуля управления источника, можно использовать пакетную операцию на обработку же операция системы управления версиями в нескольких проектах или несколько контекстов соединений. Пакеты можно использовать для устранения избыточных, диалоговые окна работу пользователей на проект.  
  
 Если пользователь выбирает несколько элементов, принадлежащих больше одного соединения в подключаемый модуль системы управления версиями, созданное с помощью подключаемого модуля API источника управления 1.1, (например, два веб-проектов на компьютерах разных общую папку) и проверяет их, пользователь видит же диалоговое окно несколько раз. Это происходит, даже если пользователь нажимает кнопку **применить ко всем** флажок в диалоговом окне, так как в Интегрированной среде разработки сбрасывает свое состояние для каждого контекста соединения.  
  
## <a name="new-capability-flag"></a>Новые возможности флаг  
 `SccBeginBatch`Функции наборов `SCC_CAP_BATCH` флаг, указывающий, что пакетная операция идет  
  
## <a name="new-functions"></a>Новые функции  
 Следующие новые функции поддерживают пакетную операцию.  
  
-   [SccBeginBatch](../../extensibility/sccbeginbatch-function.md)  
  
-   [SccEndBatch](../../extensibility/sccendbatch-function.md)  
  
 `SCCBeginBatch` Начинается с функции группы операций системы управления версиями. `SccEndBatch`Закрывает группе. Группы не могут быть вложенными.  
  
## <a name="see-also"></a>См. также  
 [Новые возможности в API версии 1.2 подключаемого модуля системы управления версиями](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)