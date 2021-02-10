---
title: Вложение на основе запуска | Документация Майкрософт
description: Сведения о вложении на основе запуска в программу, которая выполняется автоматически и соответствует пути, аналогичному назначению для ручного вложения.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, launching
- debug engines, attaching to programs
ms.assetid: 362f00ac-1909-4a3a-bacb-c0ceb5549816
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1f898bcb040b5b46144fd7c4f3fc2260b480872d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99945946"
---
# <a name="launch-based-attachment"></a>Вложение на основе запуска
Вложение на основе запуска для программы является автоматическим. Если процесс, в котором размещается программа, запускается SDM, то во вложении на основе запуска следует путь, аналогичный методу ручного вложения. Дополнительные сведения см. в разделе [Присоединение к программе](../../extensibility/debugger/attaching-to-the-program.md).

## <a name="the-attaching-process"></a>Присоединение процесса
 Основное отличие заключается в последовательности событий, следующих за вызовом **attach** , как показано ниже.

1. Отправка объекта события **IDebugEngineCreateEvent2** в SDM. Дополнительные сведения см. в разделе [Отправка событий](../../extensibility/debugger/sending-events.md).

2. Вызовите `IDebugProgram2::GetProgramId` метод для интерфейса **IDebugProgram2** , переданного методу **attach** .

3. Отправьте объект события **IDebugProgramCreateEvent2** , чтобы уведомить SDM о том, что локальный объект **IDebugProgram2** был создан для представления программы в de.

4. Отправьте объект события [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) , чтобы УВЕДОМИТь SDM о том, что для запущенного процесса был создан новый поток.

## <a name="see-also"></a>См. также раздел
- [Отправка необходимых событий](../../extensibility/debugger/sending-the-required-events.md)
- [Включение отладки программы](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
