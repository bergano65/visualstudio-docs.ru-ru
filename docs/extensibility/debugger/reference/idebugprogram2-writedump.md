---
title: IDebugProgram2::WriteDump | Документация Майкрософт
ms.date: 11/04/2016
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
ms.openlocfilehash: d7282a7bd57397f6dc1a09dac44dfb0cdfcf9078
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53915972"
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
 [in] Записываются в URL-адрес. Как правило, это в виде `file://c:\path\filename.ext`, но может быть любой допустимый URL-адрес.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Программа дампа обычно будет включать текущий кадр стека, сам стек, список потоков, выполняющих в программы и возможно, программа, которой принадлежит память.  
  
## <a name="see-also"></a>См. также  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)