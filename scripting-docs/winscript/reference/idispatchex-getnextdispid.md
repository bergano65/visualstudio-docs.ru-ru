---
title: 'IDispatchEx:: Жетнекстдиспид | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.GetNextDispID
apilocation:
- scrobj.dll
helpviewer_keywords:
- GetNextDispID method
ms.assetid: 8263d441-85ee-47f4-bdba-fbf2ad07e85f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8811e828a6701769badf45ca7c37f9c53529150f
ms.sourcegitcommit: d281d2a04a5bc302650eebf369946d8f101e59dd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/12/2020
ms.locfileid: "88144433"
---
# <a name="idispatchexgetnextdispid"></a>IDispatchEx::GetNextDispID

Перечисляет элементы объекта.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetNextDispID(
   DWORD grfdex,
   DISPID id,
   DISPID *pid
);
```

## <a name="parameters"></a>Параметры

`grfdex`\
Определяет набор элементов для перечисления. Это может быть сочетание следующих значений:

|Значение|Значение|
|-----------|-------------|
|фдексенумдефаулт|Запрашивает, что объект перечисляет элементы по умолчанию. Объекту разрешено перечислить любой набор элементов.|
|фдексенумалл|Запрашивает, что объект перечисляет все элементы. Объекту разрешено перечислить любой набор элементов.|

`id`\
Определяет текущий элемент. Жетнекстдиспид извлекает элемент в перечислении после этого. Для получения этого идентификатора использует Жетдиспид или предыдущий вызов Жетнекстдиспид. Использует значение DISPID_STARTENUM для получения первого идентификатора первого элемента.

`pid`\
Адрес переменной DISPID, которая получает идентификатор следующего элемента в перечислении.

Если элемент удален с помощью `DeleteMemberByName` или `DeleteMemberByDispID` , компонент `DISPID` должен оставаться действительным для `GetNextDispID` .

## <a name="return-value"></a>Возвращаемое значение

Возвращает одно из следующих значений:

|Значение|Значение|
|-|-|
|`S_OK`|Успех.|
|`S_FALSE`|Перечисление выполнено.|

## <a name="example"></a>Пример

```cpp
   HRESULT hr;
   BSTR bstrName;
   DISPID dispid;
   IDispatchEx *pdex;

   // Assign to pdex
   hr = pdex->GetNextDispID(fdexEnumAll, DISPID_STARTENUM, &dispid);
   while (hr == NOERROR)
   {
      hr = pdex->GetMemberName(dispid, &bstrName);
      if (!wcscmp(bstrName, OLESTR("Bar")))
      {
         SysFreeString(bstrName);
         return TRUE;
      }
      SysFreeString(bstrName);
      hr = pdex->GetNextDispID(fdexEnumAll, dispid, &dispid);
   }
```

## <a name="see-also"></a>См. также раздел

- [Интерфейс IDispatchEx](../../winscript/reference/idispatchex-interface.md)
- [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)
- [IDispatchEx::DeleteMemberByName](../../winscript/reference/idispatchex-deletememberbyname.md)
- [IDispatchEx::DeleteMemberByDispID](../../winscript/reference/idispatchex-deletememberbydispid.md)