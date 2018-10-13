---
title: IDebugProgram2::WriteDump | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProgram2::WriteDump
helpviewer_keywords:
- IDebugProgram2::WriteDump
ms.assetid: 375afb8c-882d-44db-bfa7-e2c9eb555122
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 42506dc9e4d9fdd0d85f697c4ea667705fa2b6be
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49190103"
---
# <a name="idebugprogram2writedump"></a>IDebugProgram2::WriteDump
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Записывает в файл дампа.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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

