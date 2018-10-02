---
title: Включение программы для отладки | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], enabling for programs
ms.assetid: 61d24820-0cd9-48b6-8674-6813f7493237
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f0dcb98df8562a5f35fc0d56d5a4ef6570021664
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47571532"
---
# <a name="enabling-a-program-to-be-debugged"></a>Включение программы для отладки
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [Включение программы для отладки](https://docs.microsoft.com/visualstudio/extensibility/debugger/enabling-a-program-to-be-debugged).  
  
Прежде, чем ваш модуль отладки (DE) можно отлаживать программы, необходимо сначала запустить DE или присоединить ее к существующей программы.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Получение порта](../../extensibility/debugger/getting-a-port.md)  
 В этой статье описывается получение порта на первом этапе, чтобы Включение программы для отладки.  
  
 [Регистрация программы](../../extensibility/debugger/registering-the-program.md)  
 Объясняет, следующим шагом Включение программы для отладки: регистрировать его через порт. После регистрации можно отлаживать программы, процесс присоединения или отладки just-in-time (JIT).  
  
 [Присоединение к программе](../../extensibility/debugger/attaching-to-the-program.md)  
 Объясняет, следующий шаг: чтобы подключить отладчик к программе.  
  
 [Присоединение основе запуска](../../extensibility/debugger/launch-based-attachment.md)  
 Описывает вложение на основе запуска для программы, которое выполняется автоматически при запуске, SDM.  
  
 [Отправка необходимых событий](../../extensibility/debugger/sending-the-required-events.md)  
 Шаги по требуемых событий при создании модуля отладки (DE) и подключите его к программе.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Создание пользовательского модуля отладки](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Определяет модуля отладки (DE) и описание служб, реализуемых через интерфейсы DE и как они могут вызвать отладчик для перехода между различные рабочие режимы.

