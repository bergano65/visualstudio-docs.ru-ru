---
title: "IDebugObject2::IsEncOutdated | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugObject2::IsEncOutdated
helpviewer_keywords:
- IDebugObject2::IsEncOutdated method
ms.assetid: d3a8c02d-895b-478c-9957-d663130f308e
caps.latest.revision: 8
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
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 7161f3e608390e5a513faf86b2e0b7ed2459deed
ms.contentlocale: ru-ru
ms.lasthandoff: 09/26/2017

---
# <a name="idebugobject2isencoutdated"></a>IDebugObject2::IsEncOutdated
Этот метод определяет, является ли устаревшая изменить и продолжить состояние этого объекта или родительского контейнера. Пользовательских выражений не реализует этот метод и всегда возвращает `E_NOTIMPL`.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT IsEncOutdated(  
   BOOL* pfEncOutdated  
);  
```  
  
```csharp  
int IsEncOutdated(  
   out int pfEncOutdated  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pfEncOutdated`  
 [out] Ненулевое значение (`TRUE`), если изменить и продолжить состояние является устаревшим, ноль (`FALSE`) Если это не так.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
> [!NOTE]
>  Всегда должны возвращать пользовательских выражений `E_NOTIMPL`.  
  
## <a name="see-also"></a>См. также  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
