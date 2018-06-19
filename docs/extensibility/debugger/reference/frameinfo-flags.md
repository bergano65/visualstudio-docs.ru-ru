---
title: FRAMEINFO_FLAGS | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- FRAMEINFO_FLAGS
helpviewer_keywords:
- FRAMEINFO_FLAGS enumeration
ms.assetid: 41578062-8455-412a-9d8b-1e1e9dc8d52e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ca63b23e9f87e807b3eec0e3ad35ea5414ac8dc6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31107417"
---
# <a name="frameinfoflags"></a>FRAMEINFO_FLAGS
Указывает, какую информацию необходимо вернуть о кадр стека.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
enum enum_FRAMEINFO_FLAGS {  
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
public enum enum_FRAMEINFO_FLAGS {  
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
 Инициализация или использовать `m_bstrFuncName` поле.  
  
 FIF_RETURNTYPE  
 Инициализация или использовать `m_bstrReturnType` поле.  
  
 FIF_ARGS  
 Инициализация или использовать `m_bstrArgs` поле.  
  
 FIF_LANGUAGE  
 Инициализация или использовать `m_bstrLanguage` поле.  
  
 FIF_MODULE  
 Инициализация или использовать `m_bstrModule` поле.  
  
 FIF_STACKRANGE  
 Инициализация или использовать `m_addrMin` и `m_addrMax` поля (стек диапазона).  
  
 FIF_FRAME  
 Инициализация или использовать `m_pFrame` поле.  
  
 FIF_DEBUGINFO  
 Инициализация или использовать `m_fHasDebugInfo` поле.  
  
 FIF_STALECODE  
 Инициализация или использовать `m_fStaleCode` поле.  
  
 FIF_ANNOTATEDFRAME  
 Инициализация или использовать `m_fAnnotatedFrame` поле.  
  
 FIF_DEBUG_MODULEP  
 Инициализация или использовать `m_pModule` поле.  
  
 FIF_FUNCNAME_FORMAT  
 Форматирует имя функции. Результат возвращается в `m_bstrFunName` поле и никакие другие поля не заполнены.  
  
 FIF_FUNCNAME_RETURNTYPE  
 Добавляет тип возвращаемого значения для `m_bstrFuncName` поля.  
  
 FIF_FUNCNAME_ARGS  
 Добавляет аргументы `m_bstrFuncName` поля.  
  
 FIF_FUNCNAME_LANGUAGE  
 Язык, который добавляет `m_bstrFuncName` поля.  
  
 FIF_FUNCNAME_MODULE  
 Добавляет имя модуля для `m_bstrFuncName` поля.  
  
 FIF_FUNCNAME_LINES  
 Добавляет число строк для `m_bstrFuncName` поля.  
  
 FIF_FUNCNAME_OFFSET  
 Добавляет `m_bstrFuncName` поле Смещение в байтах от начала строки, если `FIF_FUNCNAME_LINES` указано. Если `FIF_FUNCNAME_LINES` не указан, или если номера строк недоступны, добавляет смещение в байтах от начала функции.  
  
 FIF_FUNCNAME_ARGS_TYPES  
 Добавляет тип каждого аргумента в `m_bstrFuncName` поле.  
  
 FIF_FUNCNAME_ARGS_NAMES  
 Добавляет имя для каждого аргумента `m_bstrFuncName` поля.  
  
 FIF_FUNCNAME_ARGS_VALUES  
 Добавляет значение каждого аргумента в `m_bstrFuncName` поле.  
  
 FIF_FUNCNAME_ARGS_ALL  
 Добавляет тип, имя и значение всех аргументов `m_bstrFuncName` поля.  
  
 FIF_ARGS_TYPES  
 Типы аргументов, извлекаются и формат.  
  
 FIF_ARGS_NAMES  
 Имена аргументов, извлекаются и формат.  
  
 FIF_ARGS_VALUES  
 Значения аргументов, извлекаются и формат.  
  
 FIF_ARGS_ALL  
 Получение и форматирование тип, имя и значение всех аргументов.  
  
 FIF_ARGS_NOFORMAT  
 Указывает, что аргументы имеют формат (например, не добавлять открывающей и закрывающей скобки списка аргументов и не добавить разделители между аргументами).  
  
 FIF_ARGS_NO_FUNC_EVAL  
 Указывает, не используется вычисление функций (свойство) при получении значения аргументов.  
  
 FIF_FILTER_NON_USER_CODE  
 Модуль отладки — отфильтровать фреймы кода, не написанный пользователем, чтобы они не включаются.  
  
 FIF_ARGS_NO_TOSTRING  
 Не разрешать `ToString()` функции оценки или форматирование при возврате аргументов функции.  
  
 FIF_DESIGN_TIME_EXPR_EVAL  
 Сведения о кадре следует принял из размещенного домена приложения, а не процесс размещения.  
  
## <a name="remarks"></a>Примечания  
 Эти флаги будут переданы [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) и [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md) методах, чтобы указать, какие поля должны быть инициализированы в [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) структур.  
  
 Эти флаги также используются для указания поля [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) структуры не используются и допустимым при возврате структуры. Эти значения могут объединяться с помощью битового оператора `OR`.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)   
 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)