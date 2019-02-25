---
title: IDebugCodeContext2::GetLanguageInfo | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCodeContext2::GetLanguageInfo
helpviewer_keywords:
- IDebugCodeContext2::GetLanguageInfo
ms.assetid: 03002ef1-9fe6-44b6-b23b-ef7b86b2b21b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e4afcb2a8fd9de89b74fccec373e71e19264fe56
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56712493"
---
# <a name="idebugcodecontext2getlanguageinfo"></a>IDebugCodeContext2::GetLanguageInfo
Получает сведения о языке для этого контекста кода.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetLanguageInfo( 
   BSTR* pbstrLanguage,
   GUID* pguidLanguage
);
```

```csharp
int GetLanguageInfo( 
   ref string pbstrLanguage,
   ref Guid pguidLanguage
);
```

#### <a name="parameters"></a>Параметры
 `pbstrLanguage`

 [in, out] Возвращает строку, содержащую имя языка, например «C++».

 `pguidLanguage`

 [in, out] Возвращает идентификатор GUID для языка кода контекста, например, `guidCPPLang`.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 По крайней мере один из параметров должен возвращать значение отличное от null.

## <a name="see-also"></a>См. также
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)