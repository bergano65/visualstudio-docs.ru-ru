---
title: 'Ипропертипроксипровидер:: Жетпропертипрокси | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IPropertyProxyProvider::GetPropertyProxy
helpviewer_keywords:
- IPropertyProxyProvider::GetPropertyProxy
ms.assetid: 3ebb7515-5bfe-48f4-9b8d-721b8f664eb6
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cc505799a0ea7571ccff41057ba9852018ddbb3e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68199462"
---
# <a name="ipropertyproxyprovidergetpropertyproxy"></a>IPropertyProxyProvider::GetPropertyProxy
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Извлекает интерфейс прокси-сервера свойства для указанного идентификатора прокси-сервера.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT GetPropertyProxy(  
   DWORD                  dwID,  
   IPropertyProxyEESide** proxy  
);  
```  
  
```csharp  
int GetPropertyProxy(  
   uint                     dwID,  
   out IPropertyProxyEESide proxy  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `dwID`  
 окне ИДЕНТИФИКАТОР прокси-сервера требуемого свойства.  
  
 `proxy`  
 заполняет Возвращает объект [ипропертипроксеесиде](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) .  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Для поддержки визуализаторов внешних типов этот метод обычно пересылает вызов методу [жетпропертипрокси](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md) . Сведения о получении Иивисуализерсервице см. в разделе [визуализация и просмотр данных](../../../extensibility/debugger/visualizing-and-viewing-data.md) .  
  
## <a name="see-also"></a>См. также:  
 [ипропертипроксипровидер](../../../extensibility/debugger/reference/ipropertyproxyprovider.md)   
 [ипропертипроксеесиде](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [жетпропертипрокси](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)   
 [Визуализация и просмотр данных](../../../extensibility/debugger/visualizing-and-viewing-data.md)
