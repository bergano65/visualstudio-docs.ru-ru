---
title: IDebugDocument2::GetName | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocument2::GetName
helpviewer_keywords:
- IDebugDocument2::GetName
ms.assetid: 6f09ff09-b0cf-4472-8fc8-143991f0ceb1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1e653f7f735be43f2edeb4bd3c7935d3c89a9e58
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2019
ms.locfileid: "66204753"
---
# <a name="idebugdocument2getname"></a>IDebugDocument2::GetName
Возвращает имя документа в одну из нескольких форм.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetName( 
   GETNAME_TYPE gnType,
   BSTR*        pbstrFileName
);
```

```csharp
int GetName( 
   enum_GETNAME_TYPE gnType,
   out string        pbstrFileName
);
```

## <a name="parameters"></a>Параметры
`gnType`\
[in] Значение из [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md) перечисление, определяющее тип имени для возврата.

`pbstrFileName`\
[out] Возвращает строку, содержащую имя документа.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Этот метод можно например, возвращать имя документа, как заголовок или имя файла или даже частью имени файла.

## <a name="see-also"></a>См. также
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
- [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md)