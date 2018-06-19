---
title: IDebugProgram2::WriteDump | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgram2::WriteDump
helpviewer_keywords:
- IDebugProgram2::WriteDump
ms.assetid: 375afb8c-882d-44db-bfa7-e2c9eb555122
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0b17d75ace19ac53cbcd229d7c15de573c1ecb8b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31114512"
---
# <a name="idebugprogram2writedump"></a>IDebugProgram2::WriteDump
Записывает в файл дампа.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT WriteDump(   
   DUMPTYPE  DumpType,  
   LPCOLESTR pszDumpUrl  
);  
```  
  
```csharp  
int WriteDump(   
   enum_DUMPTYPE  DumpType,  
   string         pszDumpUrl  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `DumpType`  
 [in] Значение из [DUMPTYPE](../../../extensibility/debugger/reference/dumptype.md) перечисление, указывающее тип дампа, например, short или long.  
  
 `pszDumpUrl`  
 [in] Записать дамп для URL-адрес. Как правило, это в виде `file://c:\path\filename.ext`, но может быть любой допустимый URL-адрес.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Программа дампа обычно включает текущий кадр стека, сам стек, список потоков, выполняемых программой и возможно память, которому принадлежит программы.  
  
## <a name="see-also"></a>См. также  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)