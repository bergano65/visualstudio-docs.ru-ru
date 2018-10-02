---
title: IDebugProcess2::GetName | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProcess2::GetName
helpviewer_keywords:
- IDebugProcess2::GetName
ms.assetid: a2f66ab5-53e5-4cdc-a1b5-3b8afa8ee646
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 878229a56f537656fc89db92d08f1c40ace63157
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47559183"
---
# <a name="idebugprocess2getname"></a>IDebugProcess2::GetName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDebugProcess2::GetName](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugprocess2-getname).  
  
Возвращает заголовок, понятное имя или имя файла процесса.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT GetName(   
   GETNAME_TYPE  gnType,  
   BSTR*         pbstrName  
);  
```  
  
```csharp  
int GetName(   
   enum_GETNAME_TYPE  gnType,  
   out string         pbstrName  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `gnType`  
 [in] Значение из [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md) перечисления, указывающее, какой тип имени для возврата.  
  
 `pbstrName`  
 [out] Возвращает имя процесса.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md)

