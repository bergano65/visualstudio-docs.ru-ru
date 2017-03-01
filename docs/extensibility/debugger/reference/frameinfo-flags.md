---
title: "FRAMEINFO_FLAGS | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- FRAMEINFO_FLAGS
helpviewer_keywords:
- FRAMEINFO_FLAGS enumeration
ms.assetid: 41578062-8455-412a-9d8b-1e1e9dc8d52e
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 9b06b64244d34552c986c26b5df8131f30ef9d06
ms.lasthandoff: 02/22/2017

---
# <a name="frameinfoflags"></a>FRAMEINFO_FLAGS
Определяет сведения для получения о кадр стека.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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
  
```c#  
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
  
## <a name="members"></a>Члены  
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
 Инициализация и использование `m_addrMin` и `m_addrMax` поля (стек диапазон).  
  
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
 Форматы имени функции. Результат возвращается в `m_bstrFunName` поля и другие поля не заполнены.  
  
 FIF_FUNCNAME_RETURNTYPE  
 Добавляет тип, возвращаемый для `m_bstrFuncName` поля.  
  
 FIF_FUNCNAME_ARGS  
 Добавляет аргументы `m_bstrFuncName` поле.  
  
 FIF_FUNCNAME_LANGUAGE  
 Язык, который добавляет `m_bstrFuncName` поле.  
  
 FIF_FUNCNAME_MODULE  
 Добавляет имя модуля для `m_bstrFuncName` поля.  
  
 FIF_FUNCNAME_LINES  
 Добавляет число строк `m_bstrFuncName` поле.  
  
 FIF_FUNCNAME_OFFSET  
 Добавляет `m_bstrFuncName` поле Смещение в байтах от начала строки, если `FIF_FUNCNAME_LINES` указано. Если `FIF_FUNCNAME_LINES` не указан, или если номера строк не будут доступны, добавляет смещение в байтах от начала функции.  
  
 FIF_FUNCNAME_ARGS_TYPES  
 Добавляет тип каждого аргумента в `m_bstrFuncName` поле.  
  
 FIF_FUNCNAME_ARGS_NAMES  
 Добавляет имя для каждого аргумента `m_bstrFuncName` поле.  
  
 FIF_FUNCNAME_ARGS_VALUES  
 Добавляет значение каждого аргумента в `m_bstrFuncName` поле.  
  
 FIF_FUNCNAME_ARGS_ALL  
 Добавляет тип, имя и значение всех аргументов `m_bstrFuncName` поле.  
  
 FIF_ARGS_TYPES  
 Типы аргументов, извлекаются и формат.  
  
 FIF_ARGS_NAMES  
 Имена аргументов, извлекаются и формат.  
  
 FIF_ARGS_VALUES  
 Значения аргументов, извлекаются и формат.  
  
 FIF_ARGS_ALL  
 Получение и форматирование тип, имя и значение всех аргументов.  
  
 FIF_ARGS_NOFORMAT  
 Указывает, что аргументы не быть отформатированы (например, не Добавьте открывающую и закрывающую скобки вокруг списка аргументов и не добавить разделители между аргументами).  
  
 FIF_ARGS_NO_FUNC_EVAL  
 Указывает, не используется вычисление функции (свойство) при получении значения аргументов.  
  
 FIF_FILTER_NON_USER_CODE  
 Ядро отладки — для фильтрации кадров непользовательском коде, так что они не включены.  
  
 FIF_ARGS_NO_TOSTRING  
 Не разрешать `ToString()` функции оценки или форматирования при возврате аргументов функции.  
  
 FIF_DESIGN_TIME_EXPR_EVAL  
 Сведения о кадре должен полученную со размещенной домена приложения, а не главный процесс.  
  
## <a name="remarks"></a>Примечания  
 Эти флаги, передаваемые [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) и [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md) методы, чтобы указать, какие поля должны быть инициализированы в [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) структур.  
  
 Эти флаги также используются для указания поля [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) структуры используются и допустимым при возвращении структуры. Эти значения могут объединяться с помощью побитовой операции `OR`.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)   
 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)
