---
title: 'IDebugCodeContext2:: Жетлангуажеинфо | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCodeContext2::GetLanguageInfo
helpviewer_keywords:
- IDebugCodeContext2::GetLanguageInfo
ms.assetid: 03002ef1-9fe6-44b6-b23b-ef7b86b2b21b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6719968d2e828340b16f84f3195f722803d8d9d8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99928735"
---
# <a name="idebugcodecontext2getlanguageinfo"></a>IDebugCodeContext2::GetLanguageInfo
Возвращает сведения о языке для данного контекста кода.

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

## <a name="parameters"></a>Параметры
`pbstrLanguage`\
[вход, выход] Возвращает строку, содержащую имя языка, например "C++".

`pguidLanguage`\
[вход, выход] Возвращает идентификатор GUID для языка контекста кода, например `guidCPPLang` .

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 По крайней мере один из параметров должен возвращать значение, отличное от NULL.

## <a name="see-also"></a>См. также раздел
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
