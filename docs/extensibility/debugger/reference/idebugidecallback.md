---
title: IDebugIDECallback Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugIDECallback interface
ms.assetid: 8d31adc0-1c44-4658-8d4f-f4b73e35f4a6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 585ff354cef9686097325ea4dea25cd08c4cbb1b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727829"
---
# <a name="idebugidecallback"></a>IDebugIDECallback
> [!IMPORTANT]
> В Visual Studio 2015 этот способ внедрения оценщиков экспресс-выражений унижается. Для получения информации о реализации оценщиков экспрессии CLR, пожалуйста, ознакомьтесь с [clR Expression Evaluators](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [образцом управляемого оценщика экспрессии.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

 Позволяет оценщику выражения (EE) отображать сообщение в окне вывода отладчика.

## <a name="syntax"></a>Синтаксис

```
IDebugIDECallback : IUnknown
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Этот обратный вызов реализован управляемым движком отладки.

## <a name="notes-for-callers"></a>Заметки для абонентов
 Он может быть использован оценщиком выражения для отправки вывода в выходное окно отладчика.

## <a name="methods"></a>Методы
 Этот интерфейс реализует следующий метод:

|Метод|Описание|
|------------|-----------------|
|[DisplayMessage](../../../extensibility/debugger/reference/idebugidecallback-displaymessage.md)|Отправляет указанную строку сообщения в выходное окно отладчика.|

## <a name="requirements"></a>Требования
 Заголовок: Ee.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll
