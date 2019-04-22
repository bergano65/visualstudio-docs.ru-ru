---
title: IDispatchEx::GetNextDispID | Документация Майкрософт
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
ms.openlocfilehash: 4d964a8744f1f0a28704dd0a1d5e0fd2e67aab1c
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "58897677"
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
Определяет, какой набор элементов для перечисления. Это может быть сочетанием следующих значений:

|Значение|Значение|
|-----------|-------------|
|fdexEnumDefault|Запросы, что объект перечисляет элементы по умолчанию. Объект может перечислить любой набор элементов.|
|fdexEnumAll|Запросы, что объект перечисляет все элементы. Объект может перечислить любой набор элементов.|

`id`\
Определяет текущий элемент. Getnextdispid — извлекает элемент после этого перечисления. Использует getdispid — или предыдущего вызова getnextdispid — для получения идентификатора. Использует значение DISPID_STARTENUM, чтобы получить первый идентификатор первого элемента.

`pid`\
Адрес переменной DISPID, получающий идентификатор следующего элемента в перечислении.

Если удаляется элемент `DeleteMemberByName` или `DeleteMemberByDispID`, `DISPID` должен быть допустимым для `GetNextDispID`.

## <a name="return-value"></a>Возвращаемое значение

Возвращает одно из следующих значений:

|||
|-|-|
|`S_OK`|Выполнено.|
|`S_FALSE`|Выполнено перечисление.|

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

## <a name="see-also"></a>См. также

- [Интерфейс IDispatchEx](../../winscript/reference/idispatchex-interface.md)
- [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)
- [IDispatchEx::DeleteMemberByName](../../winscript/reference/idispatchex-deletememberbyname.md)
- [IDispatchEx::DeleteMemberByDispID](../../winscript/reference/idispatchex-deletememberbydispid.md)