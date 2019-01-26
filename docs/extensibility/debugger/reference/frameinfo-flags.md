---
title: FRAMEINFO_FLAGS | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- FRAMEINFO_FLAGS
helpviewer_keywords:
- FRAMEINFO_FLAGS enumeration
ms.assetid: 41578062-8455-412a-9d8b-1e1e9dc8d52e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f739061217f3265945bead95e40129b86a173f8b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54992923"
---
# <a name="frameinfoflags"></a>FRAMEINFO_FLAGS
Указывает сведения для получения о кадр стека.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
enum enum_FRAMEINFO_FLAGS {  
   FIF_FUNCNAME              = 0x00000001,  
   FIF_RETURNTYPE            = 0x00000002,  
   FIF_ARGS                  = 0x00000004,  
   FIF_LANGUAGE              = 0x00000008,  
   FIF_MODULE                = 0x00000010,  
   FIF_STACKRANGE            = 0x00000020,  
   FIF_FRAME                 = 0x00000040,  
   FIF_DEBUGINFO             = 0x00000080,  
   FIF_STALECODE             = 0x00000100,  
   FIF_ANNOTATEDFRAME        = 0x00000200,  
   FIF_DEBUG_MODULEP         = 0x00000400,  
   FIF_FUNCNAME_FORMAT       = 0x00001000,  
   FIF_FUNCNAME_RETURNTYPE   = 0x00002000,  
   FIF_FUNCNAME_ARGS         = 0x00004000,  
   FIF_FUNCNAME_LANGUAGE     = 0x00008000,  
   FIF_FUNCNAME_MODULE       = 0x00010000,  
   FIF_FUNCNAME_LINES        = 0x00020000,  
   FIF_FUNCNAME_OFFSET       = 0x00040000,  
   FIF_FUNCNAME_ARGS_TYPES   = 0x00100000,  
   FIF_FUNCNAME_ARGS_NAMES   = 0x00200000,  
   FIF_FUNCNAME_ARGS_VALUES  = 0x00400000,  
   FIF_FUNCNAME_ARGS_ALL     = 0x00700000,  
   FIF_ARGS_TYPES            = 0x01000000,  
   FIF_ARGS_NAMES            = 0x02000000,  
   FIF_ARGS_VALUES           = 0x04000000,  
   FIF_ARGS_ALL              = 0x07000000,  
   FIF_ARGS_NOFORMAT         = 0x08000000,  
   FIF_ARGS_NO_FUNC_EVAL     = 0x10000000,  
   FIF_FILTER_NON_USER_CODE  = 0x20000000,  
   FIF_ARGS_NO_TOSTRING      = 0x40000000,  
   FIF_DESIGN_TIME_EXPR_EVAL = 0x80000000  
};  
typedef DWORD FRAMEINFO_FLAGS;  
```  
  
```csharp  
public enum enum_FRAMEINFO_FLAGS {  
   FIF_FUNCNAME              = 0x00000001,  
   FIF_RETURNTYPE            = 0x00000002,  
   FIF_ARGS                  = 0x00000004,  
   FIF_LANGUAGE              = 0x00000008,  
   FIF_MODULE                = 0x00000010,  
   FIF_STACKRANGE            = 0x00000020,  
   FIF_FRAME                 = 0x00000040,  
   FIF_DEBUGINFO             = 0x00000080,  
   FIF_STALECODE             = 0x00000100,  
   FIF_ANNOTATEDFRAME        = 0x00000200,  
   FIF_DEBUG_MODULEP         = 0x00000400,  
   FIF_FUNCNAME_FORMAT       = 0x00001000,  
   FIF_FUNCNAME_RETURNTYPE   = 0x00002000,  
   FIF_FUNCNAME_ARGS         = 0x00004000,  
   FIF_FUNCNAME_LANGUAGE     = 0x00008000,  
   FIF_FUNCNAME_MODULE       = 0x00010000,  
   FIF_FUNCNAME_LINES        = 0x00020000,  
   FIF_FUNCNAME_OFFSET       = 0x00040000,  
   FIF_FUNCNAME_ARGS_TYPES   = 0x00100000,  
   FIF_FUNCNAME_ARGS_NAMES   = 0x00200000,  
   FIF_FUNCNAME_ARGS_VALUES  = 0x00400000,  
   FIF_FUNCNAME_ARGS_ALL     = 0x00700000,  
   FIF_ARGS_TYPES            = 0x01000000,  
   FIF_ARGS_NAMES            = 0x02000000,  
   FIF_ARGS_VALUES           = 0x04000000,  
   FIF_ARGS_ALL              = 0x07000000,  
   FIF_ARGS_NOFORMAT         = 0x08000000,  
   FIF_ARGS_NO_FUNC_EVAL     = 0x10000000,  
   FIF_FILTER_NON_USER_CODE  = 0x20000000,  
   FIF_ARGS_NO_TOSTRING      = 0x40000000,  
   FIF_DESIGN_TIME_EXPR_EVAL = 0x80000000  
};  
```  
  
## <a name="members"></a>Участники  
 FIF_FUNCNAME  
 Инициализация и использование `m_bstrFuncName` поля.  
  
 FIF_RETURNTYPE  
 Инициализация и использование `m_bstrReturnType` поля.  
  
 FIF_ARGS  
 Инициализация и использование `m_bstrArgs` поля.  
  
 FIF_LANGUAGE  
 Инициализация и использование `m_bstrLanguage` поля.  
  
 FIF_MODULE  
 Инициализация и использование `m_bstrModule` поля.  
  
 FIF_STACKRANGE  
 Инициализация и использование `m_addrMin` и `m_addrMax` поля (stack диапазона).  
  
 FIF_FRAME  
 Инициализация и использование `m_pFrame` поля.  
  
 FIF_DEBUGINFO  
 Инициализация и использование `m_fHasDebugInfo` поля.  
  
 FIF_STALECODE  
 Инициализация и использование `m_fStaleCode` поля.  
  
 FIF_ANNOTATEDFRAME  
 Инициализация и использование `m_fAnnotatedFrame` поля.  
  
 FIF_DEBUG_MODULEP  
 Инициализация и использование `m_pModule` поля.  
  
 FIF_FUNCNAME_FORMAT  
 Форматирует имя функции. Результат возвращается в `m_bstrFunName` поля и другие поля не заполнены.  
  
 FIF_FUNCNAME_RETURNTYPE  
 Добавляет тип возвращаемого значения на `m_bstrFuncName` поля.  
  
 FIF_FUNCNAME_ARGS  
 Добавляет аргументы `m_bstrFuncName` поля.  
  
 FIF_FUNCNAME_LANGUAGE  
 Язык, который добавляет `m_bstrFuncName` поля.  
  
 FIF_FUNCNAME_MODULE  
 Добавляет имя модуля для `m_bstrFuncName` поля.  
  
 FIF_FUNCNAME_LINES  
 Добавляет число строк, которые должны `m_bstrFuncName` поля.  
  
 FIF_FUNCNAME_OFFSET  
 Добавляет `m_bstrFuncName` поле Смещение в байтах от начала строки, если `FIF_FUNCNAME_LINES` указан. Если `FIF_FUNCNAME_LINES` не указан, или если номера строк недоступны, добавляет смещение в байтах от начала функции.  
  
 FIF_FUNCNAME_ARGS_TYPES  
 Добавляет тип каждого аргумента для `m_bstrFuncName` поля.  
  
 FIF_FUNCNAME_ARGS_NAMES  
 Добавляет имя для каждого аргумента `m_bstrFuncName` поля.  
  
 FIF_FUNCNAME_ARGS_VALUES  
 Добавляет значение каждого аргумента для `m_bstrFuncName` поля.  
  
 FIF_FUNCNAME_ARGS_ALL  
 Добавляет тип, имя и значение всех аргументов `m_bstrFuncName` поля.  
  
 FIF_ARGS_TYPES  
 Типы аргументов извлекаются и отформатирован.  
  
 FIF_ARGS_NAMES  
 Имена аргументов извлекаются и отформатирован.  
  
 FIF_ARGS_VALUES  
 Значения аргументов извлекаются и отформатирован.  
  
 FIF_ARGS_ALL  
 Извлечения и форматирования типа, имя и значение всех аргументов.  
  
 FIF_ARGS_NOFORMAT  
 Указывает, что аргументы не быть отформатированы (например, не Добавьте открывающую и закрывающую скобки вокруг списка аргументов и не добавлять разделитель между аргументами).  
  
 FIF_ARGS_NO_FUNC_EVAL  
 Указывает, что вычисление функций (свойство) не следует использовать при извлечении значения аргументов.  
  
 FIF_FILTER_NON_USER_CODE  
 Модуль отладки — отфильтровать кадры не написанный пользователем код, чтобы они не включаются.  
  
 FIF_ARGS_NO_TOSTRING  
 Не разрешать `ToString()` функции оценки или форматирования при возврате аргументы функции.  
  
 FIF_DESIGN_TIME_EXPR_EVAL  
 Сведения о кадре должен быть получить из размещенного домена приложения, а не процесс размещения.  
  
## <a name="remarks"></a>Примечания  
 Эти флаги передаются [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) и [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md) методы, чтобы указать, какие поля должны быть инициализированы в [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) структурой или структурами.  
  
 Эти флаги также используются для указания поля [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) структуры не используются и допустимым при возвращении структуры. Эти значения могут объединяться с побитовым объектом `OR`.  
  
## <a name="requirements"></a>Требования  
 Header: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)   
 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)