---
title: "Включение программы для отладки | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugging [Debugging SDK], enabling for programs
ms.assetid: 61d24820-0cd9-48b6-8674-6813f7493237
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: a581c5a9ae56f52727c011db1de2ad35a5ba3592
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="enabling-a-program-to-be-debugged"></a>Включение программы для отладки
Перед ваш модуль отладки (DE) можно отлаживать программы, необходимо запустить DE или подключите его к существующей программы.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Получение порта](../../extensibility/debugger/getting-a-port.md)  
 Описывает получение порт первым этапом включения отлаживаемой программы.  
  
 [Регистрация программы](../../extensibility/debugger/registering-the-program.md)  
 Описывается включение программы для отладки к следующему шагу: зарегистрировав его с портом. После регистрации можно отлаживать программы либо в процессе присоединения или время JIT-отладки.  
  
 [Присоединение к программе](../../extensibility/debugger/attaching-to-the-program.md)  
 Объясняет следующий шаг: присоединить отладчик к программе.  
  
 [На основе запуска присоединение](../../extensibility/debugger/launch-based-attachment.md)  
 Описывает запуск под управлением вложение в программу, которая выполняется автоматически при запуске с SDM.  
  
 [Отправка необходимых событий](../../extensibility/debugger/sending-the-required-events.md)  
 Этапы требуемые события при создании модуля отладки (DE) и подключение к программе.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Создание пользовательского модуля отладки](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Определяет модуля отладки (DE), а также описание служб, реализуемых через интерфейсы DE и как они могут вызвать отладчик для перехода между различными режимами рабочей.