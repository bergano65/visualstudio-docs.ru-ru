---
title: Вложение на основе запуска | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, launching
- debug engines, attaching to programs
ms.assetid: 362f00ac-1909-4a3a-bacb-c0ceb5549816
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 09a6b39bef9ba6af098bf92d779a490e22492209
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203162"
---
# <a name="launch-based-attachment"></a>Вложение на основе запуска
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Вложение на основе запуска для программы является автоматическим. Если процесс, в котором размещается программа, запускается SDM, то во вложении на основе запуска следует путь, аналогичный методу ручного вложения. Дополнительные сведения см. в разделе [Присоединение к программе](../../extensibility/debugger/attaching-to-the-program.md).  
  
## <a name="the-attaching-process"></a>Присоединение процесса  
 Основное отличие заключается в последовательности событий, следующих за вызовом **attach** , как показано ниже.  
  
1. Отправка объекта события **IDebugEngineCreateEvent2** в SDM. Дополнительные сведения см. в разделе [Отправка событий](../../extensibility/debugger/sending-events.md).  
  
2. Вызовите `IDebugProgram2::GetProgramId` метод для интерфейса **IDebugProgram2** , переданного методу **attach** .  
  
3. Отправьте объект события **IDebugProgramCreateEvent2** , чтобы уведомить SDM о том, что локальный объект **IDebugProgram2** был создан для представления программы в de.  
  
4. Отправьте объект события [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) , чтобы УВЕДОМИТь SDM о том, что для запущенного процесса был создан новый поток.  
  
## <a name="see-also"></a>См. также:  
 [Отправка необходимых событий](../../extensibility/debugger/sending-the-required-events.md)   
 [Включение программы для отладки](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
