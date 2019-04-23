---
title: IDebugStackFrame2::GetLanguageInfo | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetLanguageInfo
helpviewer_keywords:
- IDebugStackFrame2::GetLanguageInfo
ms.assetid: 0e12fd92-f155-46a7-8272-cda279388cfb
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d370670ed86ee3484243fe5dc7cfdd8ea64be084
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60055905"
---
# <a name="idebugstackframe2getlanguageinfo"></a>IDebugStackFrame2::GetLanguageInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Возвращает язык, связанный с данным кадром стека.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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
  
#### <a name="parameters"></a>Параметры  
 `pbstrLanguage`  
 [out] Возвращает имя языка, который реализует метод, связанный с данным кадром стека.  
  
 `pguidLanguage`  
 [out] Возвращает `GUID` языка. Для [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] языков, например, следующие могут быть возвращены:  
  
- `guidVBScriptLang`  
  
- `guidJScriptLang`  
  
- `guidCPPLang`  
  
- `guidVBLang`  
  
- `guidSQLLang`  
  
- `guidScriptLang`  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
