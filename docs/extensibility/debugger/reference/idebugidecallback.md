---
title: IDebugIDECallback | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugIDECallback interface
ms.assetid: 8d31adc0-1c44-4658-8d4f-f4b73e35f4a6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bdbc1cc5a8f7534f2ee11699d67b4128796602c6
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63413984"
---
# <a name="idebugidecallback"></a>IDebugIDECallback
> [!IMPORTANT]
> В Visual Studio 2015 таким образом, реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [управляемых образец средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Позволяет вычислитель выражений (EE) для отображения сообщения в окне вывода отладчика.

## <a name="syntax"></a>Синтаксис

```
IDebugIDECallback : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Этот обратный вызов реализуется Подсистема управляемой отладки.

## <a name="notes-for-callers"></a>Заметки о вызывающих объектов
 Он может использоваться в вычислитель выражений для отправки выходных данных в окне вывода отладчика.

## <a name="methods"></a>Методы
 Этот интерфейс реализует следующий метод:

|Метод|Описание|
|------------|-----------------|
|[DisplayMessage](../../../extensibility/debugger/reference/idebugidecallback-displaymessage.md)|Отправляет заданной строкой сообщения в окне вывода отладчика.|

## <a name="requirements"></a>Требования
 Заголовок: EE.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll