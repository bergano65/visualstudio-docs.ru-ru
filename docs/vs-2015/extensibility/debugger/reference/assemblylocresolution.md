---
title: АССЕМБЛИЛОКРЕСОЛУТИОН | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- ASSEMBLYLOCRESOLUTION
helpviewer_keywords:
- ASSEMBLYLOCRESOLUTION enumeration
ms.assetid: 0bcfe85c-5f37-4a9d-bf2b-141acd96ad67
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c088b27e686d42d800a6470fbbced8192c100bfc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153597"
---
# <a name="assemblylocresolution"></a>ASSEMBLYLOCRESOLUTION
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Указывает, где находится сборка.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
enum enum_ASSEMBLYLOCRESOLUTION {  
   ALR_NAME      = 0x0,  
   ALR_USERDIR   = 0x1,  
   ALR_SHAREDDIR = 0x2,  
   ALR_REMOTEDIR = 0x4,  
};  
typedef DWORD ASSEMBLYLOCRESOLUTION;  
```  
  
```csharp  
public enum enum_ASSEMBLYLOCRESOLUTION {  
   ALR_NAME      = 0x0,  
   ALR_USERDIR   = 0x1,  
   ALR_SHAREDDIR = 0x2,  
   ALR_REMOTEDIR = 0x4,  
};  
```  
  
## <a name="members"></a>Участники  
 ALR_NAME  
 Сборка находится в текущем пространстве имен.  
  
 ALR_USERDIR  
 Сборка находится в каталоге пользователя.  
  
 ALR_SHAREDDIR  
 Сборка находится в общем каталоге.  
  
 ALR_REMOTEDIR  
 Сборка находится в удаленном каталоге.  
  
## <a name="remarks"></a>Remarks  
 Эти значения возвращаются методами [ресолвеассемблиреф](../../../extensibility/debugger/reference/ipropertyproxyeeside-resolveassemblyref.md) и [жетманажедвиеверкреатиондата](../../../extensibility/debugger/reference/ipropertyproxyeeside-getmanagedviewercreationdata.md) .  
  
 Эти значения можно сочетать с `OR` операцией.  
  
## <a name="requirements"></a>Требования  
 Заголовок: мсдбг. h  
  
 Пространство имен: Microsoft. VisualStudio. Debugger. Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также:  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [ресолвеассемблиреф](../../../extensibility/debugger/reference/ipropertyproxyeeside-resolveassemblyref.md)   
 [GetManagedViewerCreationData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getmanagedviewercreationdata.md)
