---
title: IDebugДокументЧексум2 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentChecksum2 interface
ms.assetid: 6d22fa94-21aa-46cb-b5b5-32a6399ebb20
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 03cfb29cc54a2f0ab18bce3ec0761cfab62e20df
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731895"
---
# <a name="idebugdocumentchecksum2"></a>IDebugDocumentChecksum2
Представляет проверку для отладки документа и позволяет передавать чекмежду через компоненты.

## <a name="syntax"></a>Синтаксис

```
IDebugDocumentChecksum2 : IUnknown
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Этот интерфейс может быть реализован любым компонентом, который предоставляет интерфейс [IDebugDocumentContext2.](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) Тем не менее, он в основном реализован двигателями отладки, так что чековая сумма, встроенная в файл символа (к.pdb), может быть передана обратно в IDE и использована при поиске источника.

## <a name="methods"></a>Методы
 В следующей таблице показаны методы `IDebugDocumentChecksum2`.

|Метод|Описание|
|------------|-----------------|
|[GetChecksumAndAlgorithmId](../../../extensibility/debugger/reference/idebugdocumentchecksum2-getchecksumandalgorithmid.md)|Извлекает проверку документа и идентификатор алгоритма с учетом максимального количества байтов для использования.|

## <a name="requirements"></a>Требования
 Заголовок: Msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll
