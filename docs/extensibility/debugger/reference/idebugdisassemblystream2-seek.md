---
title: IDebugDisassemblyStream2::Seek | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::Seek
helpviewer_keywords:
- IDebugDisassemblyStream2::Seek
ms.assetid: afec3008-b1e0-4803-ad24-195dbfb6497e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f0763a4191f011748c6c5145a250459c4b9b4cf8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62921722"
---
# <a name="idebugdisassemblystream2seek"></a>IDebugDisassemblyStream2::Seek
Перемещает указатель чтения в потоке дизассемблированного кода заданного числа инструкции относительно указанной позиции.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT Seek( 
   SEEK_START          dwSeekStart,
   IDebugCodeContext2* pCodeContext,
   UINT64              uCodeLocationId,
   INT64               iInstructions
);
```

```csharp
int Seek( 
   enum_SEEK_START    dwSeekStart,
   IDebugCodeContext2 pCodeContext,
   ulong              uCodeLocationId,
   long               iInstructions
);
```

#### <a name="parameters"></a>Параметры
 `dwSeekStart`

 [in] Значение из [SEEK_START](../../../extensibility/debugger/reference/seek-start.md) перечисление, указывающее относительное положение, чтобы начать процесс поиска.

 `pCodeContext`

 [in] [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) объект, представляющий контекст кода, относительно операции поиска. Этот параметр используется только в том случае, если `dwSeekStart`  =  `SEEK_START_CODECONTEXT`; в противном случае этот параметр игнорируется и может иметь значение null.

 `uCodeLocationId`

 [in] Идентификатор расположения кода, относительно операции поиска. Этот параметр используется в том случае, если `dwSeekStart`  =  `SEEK_START_CODELOCID`; в противном случае этот параметр игнорируется и может быть равным 0. См. в разделе "Примечания" [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md) метод описание идентификатора в расположение кода.

 `iInstructions`

 [in] Количество инструкций для перемещения относительно позиции, указанной в `dwSeekStart`. Это значение может быть отрицательным для перемещения в обратном направлении.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` если позиция поиска был в точку за пределами списка доступных команд. В противном случае возвращается код ошибки.

## <a name="remarks"></a>Примечания
 Если seek в позицию в начале списка, до первой инструкции в списке имеет значение этой позиции чтения. Если см. раздел в позицию после конца списка, положение чтения имеет значение последней инструкции в списке.

## <a name="see-also"></a>См. также
- [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)
- [SEEK_START](../../../extensibility/debugger/reference/seek-start.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)