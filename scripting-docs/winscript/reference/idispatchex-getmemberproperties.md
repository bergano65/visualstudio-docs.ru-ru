---
title: 'IDispatchEx:: Жетмемберпропертиес | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.GetMemberProperties
apilocation:
- scrobj.dll
helpviewer_keywords:
- GetMemberProperties method
ms.assetid: 20d43209-12e2-472a-9bf3-81eced137b71
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8016eef7b6e0da9b9fc88695db845cba7f608ff3
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574088"
---
# <a name="idispatchexgetmemberproperties"></a>IDispatchEx::GetMemberProperties
Извлекает свойства элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetMemberProperties(  
   DISPID id,  
   DWORD grfdexFetch,  
   DWORD *pgrfdex  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `id`  
 Идентифицирует член. Для получения идентификатора диспетчеризации использует `GetDispID` или `GetNextDispID`.  
  
 `grfdexFetch`  
 Определяет, какие свойства следует извлечь. Это может быть сочетание значений, перечисленных в разделе `pgrfdex` и/или сочетания следующих значений:  
  
|Значение|Значение|  
|-----------|-------------|  
|грфдекспропканалл|Объединяет Фдекспропканжет, Фдекспропканпут, Фдекспропканпутреф, Фдекспропканкалл, Фдекспропканконструкт и fdexPropCanSourceEvents.|  
|грфдекспропканноталл|Объединяет Фдекспропканнотжет, Фдекспропканнотпут, Фдекспропканнотпутреф, Фдекспропканноткалл, Фдекспропканнотконструкт и fdexPropCannotSourceEvents.|  
|грфдекспропекстраалл|Объединяет Фдекспропносидиффектс и Фдекспропдинамиктипе.|  
|грфдекспропалл|Объединяет Грфдекспропканалл, Грфдекспропканноталл и Грфдекспропекстраалл.|  
  
 `pgrfdex`  
 Адрес `DWORD`, который получает запрошенные свойства. Это может быть сочетание следующих значений:  
  
|Значение|Значение|  
|-----------|-------------|  
|фдекспропканжет|Элемент можно получить с помощью DISPATCH_PROPERTYGET.|  
|фдекспропканнотжет|Не удается получить элемент с помощью DISPATCH_PROPERTYGET.|  
|фдекспропканпут|Элемент можно задать с помощью DISPATCH_PROPERTYPUT.|  
|фдекспропканнотпут|Невозможно задать элемент с помощью DISPATCH_PROPERTYPUT.|  
|фдекспропканпутреф|Элемент можно задать с помощью DISPATCH_PROPERTYPUTREF.|  
|фдекспропканнотпутреф|Невозможно задать элемент с помощью DISPATCH_PROPERTYPUTREF.|  
|фдекспропносидиффектс|У элемента нет побочных эффектов. Например, отладчик может безопасно получить/установить/вызвать этот элемент, не изменяя состояние отлаживаемого скрипта.|  
|фдекспропдинамиктипе|Элемент является динамическим и может изменяться в течение времени существования объекта.|  
|фдекспропканкалл|Член можно вызвать как метод с помощью DISPATCH_METHOD.|  
|фдекспропканноткалл|Член нельзя вызвать как метод с помощью DISPATCH_METHOD.|  
|фдекспропканконструкт|Член можно вызвать как конструктор с помощью DISPATCH_CONSTRUCT.|  
|фдекспропканнотконструкт|Элемент не может быть вызван как конструктор с помощью DISPATCH_CONSTRUCT.|  
|фдекспропкансаурцеевентс|Элемент может запускать события.|  
|фдекспропканнотсаурцеевентс|Член не может порождать события.|  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает одно из следующих значений:  
  
|||  
|-|-|  
|`S_OK`|Выполнено.|  
|`DISP_E_UNKNOWNNAME`|Неизвестное имя.|  
  
## <a name="example"></a>Пример  
  
```cpp
BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;   
   DWORD dwProps;  
  
   // Assign to pdex and bstrName  
   if (SUCCEEDED(pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid)) &&  
      SUCCEEDED(pdex->GetMemberProperties(dispid, grfdexPropAll, &dwProps)) &&  
         (dwProps & fdexPropCanPut))  
   {  
      // Assign to member  
   }  
```  
  
## <a name="see-also"></a>См. также:  
   [интерфейса IDispatchEx](../../winscript/reference/idispatchex-interface.md)  
 [IDispatchEx:: жетдиспид](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)