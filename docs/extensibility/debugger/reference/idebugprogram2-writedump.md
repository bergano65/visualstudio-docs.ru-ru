---
title: "IDebugProgram2::WriteDump | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgram2::WriteDump
helpviewer_keywords: IDebugProgram2::WriteDump
ms.assetid: 375afb8c-882d-44db-bfa7-e2c9eb555122
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 40fcd345a2a07a0ebdcf9e984b060cc81e946fc3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
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