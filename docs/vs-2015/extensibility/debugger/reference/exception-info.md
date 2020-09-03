---
title: EXCEPTION_INFO | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- EXCEPTION_INFO
helpviewer_keywords:
- EXCEPTION_INFO structure
ms.assetid: d046957a-b97d-420b-b46b-c67cbaef709e
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 66af4d95707be99865df3df32751215cf5eb10b2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68181176"
---
# <a name="exception_info"></a>EXCEPTION_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Описывает исключение или ошибку времени выполнения, вызванную отлаживаемой программой.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
typedef struct tagEXCEPTION_INFO {   
   IDebugProgram2* pProgram;  
   BSTR            bstrProgramName;  
   BSTR            bstrExceptionName;  
   DWORD           dwCode;  
   EXCEPTION_STATE dwState;  
   GUID            guidType;  
} EXCEPTION_INFO;  
```  
  
```csharp  
public struct EXCEPTION_INFO {   
   public IDebugProgram2 pProgram;  
   public string         bstrProgramName;  
   public string         bstrExceptionName;  
   public uint           dwCode;  
   public uint           dwState;  
   public Guid           guidType;  
};  
```  
  
## <a name="members"></a>Участники  
 ппрограм  
 Объект [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) , представляющий программу, в которой возникло исключение.  
  
 бстрпрограмнаме  
 Имя программы, в которой возникло исключение.  
  
 бстрексцептионнаме  
 Имя исключения.  
  
 двкоде  
 Идентификационный код для исключения или ошибки времени выполнения.  
  
 двстате  
 Значение из перечисления [EXCEPTION_STATE](../../../extensibility/debugger/reference/exception-state.md) , определяющее состояние исключения.  
  
 гуидтипе  
 Идентификатор языка GUID: `guidLang` или `guidEng` .  
  
## <a name="remarks"></a>Remarks  
 Эта структура передается в качестве параметра методам [сетексцептион](../../../extensibility/debugger/reference/idebugengine2-setexception.md) и [ремовесетексцептион](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md) . Эта структура также передается в метод [except](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md) , который должен быть заполнен.  
  
## <a name="requirements"></a>Требования  
 Заголовок: мсдбг. h  
  
 Пространство имен: Microsoft. VisualStudio. Debugger. Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также:  
 [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [EXCEPTION_STATE](../../../extensibility/debugger/reference/exception-state.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [сетексцептион](../../../extensibility/debugger/reference/idebugengine2-setexception.md)   
 [ремовесетексцептион](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)   
 [GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md)
