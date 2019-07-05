---
title: IDebugDocumentChecksum2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentChecksum2 interface
ms.assetid: 6d22fa94-21aa-46cb-b5b5-32a6399ebb20
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0b4bfc51595e6414a3760d4e57ab6f9791259f83
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66341288"
---
# <a name="idebugdocumentchecksum2"></a>IDebugDocumentChecksum2
Представляет контрольную сумму для документа отладки и обеспечивает передачи контрольную сумму между компонентами.

## <a name="syntax"></a>Синтаксис

```
IDebugDocumentChecksum2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Этот интерфейс может быть реализован любой компонент, предоставляющий [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) интерфейс. Тем не менее она главным образом реализуется отладчиков, чтобы контрольная сумма, внедренных в файл символов (*.pdb) могут передаваться обратно в интегрированной среде разработки и используется при поиске источника.

## <a name="methods"></a>Методы
 В следующей таблице показаны методы `IDebugDocumentChecksum2`.

|Метод|Описание|
|------------|-----------------|
|[GetChecksumAndAlgorithmId](../../../extensibility/debugger/reference/idebugdocumentchecksum2-getchecksumandalgorithmid.md)|Извлекает идентификатор документа контрольной суммы и алгоритм Получает максимальное число байтов для использования.|

## <a name="requirements"></a>Требования
 Заголовок: Msdbg.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll