---
title: 'IDebugProcess3:: Жесостингпроцесслангуаже | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProcess3::GetHostingProcessLanguage
helpviewer_keywords:
- IDebugProcess3::GetHostingProcessLanguage
ms.assetid: 52fca002-a9ef-43b1-9192-afbe7bb59ad4
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bd338443a6cad0a772d3780c4dbf361f2634240c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202838"
---
# <a name="idebugprocess3gethostingprocesslanguage"></a>IDebugProcess3::GetHostingProcessLanguage
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот метод возвращает, `GUID` представляющий язык этого процесса, заданный с помощью вызова [сесостингпроцесслангуаже](../../../extensibility/debugger/reference/idebugprocess3-sethostingprocesslanguage.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetHostingProcessLanguage(  
   GUID* pguidLang  
);  
```  
  
```csharp  
int GetHostingProcessLanguage(  
   out Guid pguidLang  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pguidLang`  
 заполняет `GUID` Язык этого процесса. `GUID_NULL` (C++) или `Guid.Empty` (C#) означает, что язык не задан.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK` ; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также:  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [SetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-sethostingprocesslanguage.md)
