---
title: IDebugCustomViewer::DisplayValue | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCustomViewer::DisplayValue
helpviewer_keywords:
- IDebugCustomViewer::DisplayValue
ms.assetid: 7a538248-5ced-450e-97cd-13fabe35fb1c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 017e1e7a27839dae91559468c62be353bbd43b4e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31107063"
---
# <a name="idebugcustomviewerdisplayvalue"></a>IDebugCustomViewer::DisplayValue
Этот метод вызывается для отображения указанного значения.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT DisplayValue(  
   HWND             hwnd,  
   DWORD            dwID,  
   IUnknown *       pHostServices,  
   IDebugProperty3* pDebugProperty);  
);  
```  
  
```csharp  
int DisplayValue(  
   IntPtr          hwnd,   
   uint            dwID,   
   object          pHostServices,   
   IDebugProperty3 pDebugProperty  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `hwnd`  
 [in] Родительское окно  
  
 `dwID`  
 [in] Идентификатор для пользовательских средств просмотра, которые поддерживают более одного типа.  
  
 `pHostServices`  
 [in] Зарезервировано. Всегда устанавливается в значение null.  
  
 `pDebugProperty`  
 [in] Интерфейс, который может использоваться для получения значения для отображения.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Отображение является «modal», в том, что этот метод будет создать окно необходимые, отображение значения, ожидающими ввода данных и закройте окно все до возвращения вызывающему объекту. Это означает, что метод должен обрабатывать все аспекты отображения значения свойства, от создания окна для вывода на ожидание ввода пользователя, чтобы уничтожение окна.  
  
 Для поддержки изменения значения на данной [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) объекта, можно использовать [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md) метод, если значение можно выразить в виде строки. В противном случае она необходима для создания пользовательского интерфейса — только для оценки выражений, такая реализация `DisplayValue` метод — на тот же объект, реализующий `IDebugProperty3` интерфейса. Этот пользовательский интерфейс будет предоставить способы изменения данных произвольного размера и сложности.  
  
## <a name="see-also"></a>См. также  
 [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)