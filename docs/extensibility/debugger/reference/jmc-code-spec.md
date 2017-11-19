---
title: "JMC_CODE_SPEC | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: JMC_CODE_SPEC
helpviewer_keywords: JMC_CODE_SPEC structure
ms.assetid: d89498f1-4234-46d9-b4e2-abbcbca5068a
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2bfcd1f63196856eef7fa7293d9efbc07c9813a9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="jmccodespec"></a>JMC_CODE_SPEC
Эта структура используется для задания сведений JustMyCode для модуля.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
typedef struct _JMC_CODE_SPEC {  
   BOOL fIsUserCode;  
   BSTR bstrModuleName;  
} JMC_CODE_SPEC;  
```  
  
```csharp  
public struct JMC_CODE_SPEC {  
   public int    fIsUserCode;  
   public string bstrModuleName;  
};  
```  
  
## <a name="members"></a>Члены  
 fIsUserCode  
 Не равно нулю (`TRUE`), если модуль должны считаться кодом пользователя; в противном случае — ноль (`FALSE`) Если модуль следует рассматривать как внешний код и не для отладки.  
  
 bstrModuleName  
 Имя модуля в вопросе.  
  
## <a name="remarks"></a>Примечания  
 Эта структура передается как список таких структур для [SetJustMyCodeState](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md) метод.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Структур и объединений](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [SetJustMyCodeState](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md)