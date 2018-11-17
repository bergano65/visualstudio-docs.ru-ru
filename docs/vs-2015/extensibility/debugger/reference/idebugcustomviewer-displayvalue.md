---
title: IDebugCustomViewer::DisplayValue | Документация Майкрософт
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
- IDebugCustomViewer::DisplayValue
helpviewer_keywords:
- IDebugCustomViewer::DisplayValue
ms.assetid: 7a538248-5ced-450e-97cd-13fabe35fb1c
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9bf13bfea09afed15c548641873fc1b2b075dfcf
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51724291"
---
# <a name="idebugcustomviewerdisplayvalue"></a>IDebugCustomViewer::DisplayValue
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот метод вызывается для отображения указанного значения.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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
 [in] Зарезервировано. Всегда задано значение null.  
  
 `pDebugProperty`  
 [in] Интерфейс, который может использоваться для получения значения для отображения.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Отображение «modal», в том, что этот метод будет создать необходимые период, отображения значения, ожидать входные данные и закрыть окно, все перед возвратом вызывающей стороне. Это означает, что метод должен обрабатывать все аспекты отображения значения свойства, от создания окна для вывода, чтобы ожидать ввода пользователя, чтобы уничтожение окна.  
  
 Для поддержки, изменив значение на заданный [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) объекта, можно использовать [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md) метод, если значение можно выразить в виде строки. В противном случае она необходима для создания пользовательского интерфейса — исключительно для оценки выражений, такая реализация `DisplayValue` метод — на тот же объект, реализующий `IDebugProperty3` интерфейс. Этот пользовательский интерфейс будет указать методы для изменения данных произвольного размера или сложности.  
  
## <a name="see-also"></a>См. также  
 [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)

