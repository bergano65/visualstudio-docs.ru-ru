---
title: Применение параметров в нескольких подключениях к проектам | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, application of settings
ms.assetid: 2116d3d0-c46c-4d0a-b482-08a178584f46
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bca17fdc440fc373d0d4811ed57cd5d27a6c201a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203844"
---
# <a name="application-of-settings-across-multiple-project-connections"></a>Применение параметров в нескольких подключениях проекта
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Подключаемый модуль системы управления версиями, созданный с помощью подключаемого модуля управления исходным кодом API 1,2, может использовать пакетную операцию для выполнения одной и той же операции системы управления версиями в нескольких проектах или нескольких контекстах соединения. Пакеты можно использовать для исключения избыточных диалоговых окон по проекту из интерфейса пользователя.  
  
 Если пользователь выбирает несколько элементов, относящихся к нескольким соединениям в подключаемом модуле системы управления версиями, созданном с помощью API подключаемого модуля системы управления версиями 1,1 (например, два веб-проекта на разных компьютерах с общими файловыми ресурсами) и извлекает их, пользователь видит одно и то же диалоговое окно несколько раз. Это происходит, даже если пользователь нажимает флажок **Применить ко всем** в диалоговом окне, так как интегрированная среда разработки сбрасывает свое состояние для каждого контекста подключения.  
  
## <a name="new-capability-flag"></a>Новый флаг возможностей  
 `SccBeginBatch` Задает `SCC_CAP_BATCH` флаг, указывающий, что выполняется пакетная операция  
  
## <a name="new-functions"></a>Новые функции  
 Следующие новые функции поддерживают пакетную операцию:  
  
- [SccBeginBatch](../../extensibility/sccbeginbatch-function.md)  
  
- [SccEndBatch](../../extensibility/sccendbatch-function.md)  
  
  `SCCBeginBatch`Функция запускает группу операций системы управления версиями. `SccEndBatch` закрывает группу. Группы не могут быть вложенными.  
  
## <a name="see-also"></a>См. также:  
 [Новые возможности в API версии 1.2 подключаемого модуля системы управления версиями](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
