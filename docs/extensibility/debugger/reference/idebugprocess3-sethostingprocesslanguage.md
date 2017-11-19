---
title: "IDebugProcess3::SetHostingProcessLanguage | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProcess3::SetHostingProcessLanguage
helpviewer_keywords: IDebugProcess3::SetHostingProcessLanguage
ms.assetid: e42f33ed-f29c-4e45-92ce-ab504b72d77c
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b1268f6b001be1fa12febfb997011963d919a5c7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprocess3sethostingprocesslanguage"></a>IDebugProcess3::SetHostingProcessLanguage
Этот метод задает язык, процесс будет размещаться в группе. Этот язык можно использоваться ядром отладки (DE) для загрузки соответствующего выражений.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT SetHostingProcessLanguage(  
   REFGUID guidLang  
);  
```  
  
```csharp  
int SetHostingProcessLanguage(  
   ref Guid guidLang  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `guidLang`  
 [in] `GUID` языка, который следует использовать DE. Укажите `GUID_NULL` (C++) или `Guid.Empty` (C#), чтобы иметь DE использования языка по умолчанию.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 [GetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-gethostingprocesslanguage.md) может использоваться для получения текущих языковых параметров.  
  
## <a name="see-also"></a>См. также  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [GetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-gethostingprocesslanguage.md)