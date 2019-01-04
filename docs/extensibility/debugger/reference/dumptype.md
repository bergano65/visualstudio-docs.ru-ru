---
title: DUMPTYPE | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- DUMPTYPE
helpviewer_keywords:
- DUMPTYPE enumeration
ms.assetid: ea8160db-8732-4056-a1d7-892ef72da71e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 327b0e2dde4826682be2ffbd907c97369e1586e2
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53952142"
---
# <a name="dumptype"></a>DUMPTYPE
Указывает, какая часть состояния программы (например, запущенные потоки, кадров стека и текущий адрес инструкции) для помещения в дамп.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
enum enum_DUMPTYPE {   
   DUMP_MINIDUMP = 0,  
   DUMP_FULLDUMP = 1  
};  
typedef DWORD DUMPTYPE;  
```  
  
```csharp  
public enum enum_DUMPTYPE {   
   DUMP_MINIDUMP = 0,  
   DUMP_FULLDUMP = 1  
};  
```  
  
## <a name="members"></a>Участники  
 DUMP_MINIDUMP  
 Указывает Мелкая "," compact дампа.  
  
 DUMP_FULLDUMP  
 Указывает больших, полный дамп.  
  
## <a name="remarks"></a>Примечания  
 Передается в качестве аргумента для [WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md) метод.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md)