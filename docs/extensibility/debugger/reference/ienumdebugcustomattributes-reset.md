---
title: "IEnumDebugCustomAttributes::Reset | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEnumCustomAttributes::Reset
helpviewer_keywords: IEnumDebugCustomAttributes::Reset
ms.assetid: e0db6518-5a71-4adb-a407-4d2ac7a3e369
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9b593b7bcd22b5eb8c12fffb6fe277a68a9da12f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="ienumdebugcustomattributesreset"></a>IEnumDebugCustomAttributes::Reset
Сбрасывает последовательность перечисления в начало.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT Reset(void);  
```  
  
```csharp  
int Reset();  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 После вызова этого метода, при следующем вызове [Далее](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md) метод возвращает первый элемент перечисления.  
  
## <a name="see-also"></a>См. также  
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)   
 [Вперед](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md)