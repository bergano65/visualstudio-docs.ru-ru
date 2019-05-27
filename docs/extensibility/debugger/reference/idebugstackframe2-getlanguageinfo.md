---
title: IDebugStackFrame2::GetLanguageInfo | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetLanguageInfo
helpviewer_keywords:
- IDebugStackFrame2::GetLanguageInfo
ms.assetid: 0e12fd92-f155-46a7-8272-cda279388cfb
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c5b6b5a94b38e1d057e51fe8f3ad8ed8e0003e4e
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2019
ms.locfileid: "66203281"
---
# <a name="idebugstackframe2getlanguageinfo"></a>IDebugStackFrame2::GetLanguageInfo
Возвращает язык, связанный с данным кадром стека.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetLanguageInfo ( 
   BSTR* pbstrLanguage,
   GUID* pguidLanguage
);
```

```csharp
int GetLanguageInfo ( 
   ref string pbstrLanguage,
   ref Guid   pguidLanguage
);
```

## <a name="parameters"></a>Параметры
`pbstrLanguage`\
[out] Возвращает имя языка, который реализует метод, связанный с данным кадром стека.

`pguidLanguage`\
[out] Возвращает `GUID` языка. Для [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] языков, например, следующие могут быть возвращены:

-   `guidVBScriptLang`\

-   `guidJScriptLang`\

-   `guidCPPLang`\

-   `guidVBLang`\

-   `guidSQLLang`\

-   `guidScriptLang`\

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)