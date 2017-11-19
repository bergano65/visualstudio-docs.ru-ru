---
title: "IActiveScriptAuthor::GetInfoFromContext | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptAuthor.GetInfoFromContext
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptAuthor::GetInfoFromContext
ms.assetid: 9891b095-6eb5-4473-87c0-c2e5cd2afc1a
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 27c13dbe51bb1150554275b5fbeacd00be2e445f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptauthorgetinfofromcontext"></a>IActiveScriptAuthor::GetInfoFromContext
Возвращает введите сведения и позиций привязки для заданного символа в блок кода. Это дает сведения для элемента, IntelliSense, глобальных списков и подсказки по параметрам.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT GetInfoFromContext(  
   LPCOLESTR  pszCode,  
   ULONG      cchCode,  
   ULONG      ichCurrentPosition,  
   DWORD      dwListTypesRequested,  
   DWORD      *pdwListTypesProvided,  
   ULONG      *pichListAnchorPosition,  
   ULONG      *pichFuncAnchorPosition,  
   MEMBERID   *pmemid,  
   LONG       *piCurrentParameter,  
   IUnknown   **ppunk  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pszCode`  
 [in] Адрес блока строка кода, используемый для формирования результатов сведения.  
  
 `cchCode`  
 [in] Длина блока кода.  
  
 `ichCurrentPosition`  
 [in] Позиция символа относительно начала блока.  
  
 `dwListTypesRequested`  
 [in] Типы списка, запросу. Может быть сочетанием следующих значений:  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|SCRIPT_CMPL_NOLIST|0x0000|Список отсутствует.|  
|SCRIPT_CMPL_MEMBERLIST|0x0001|Список членов.|  
|SCRIPT_CMPL_ENUMLIST|0x0002|Список перечисления.|  
|SCRIPT_CMPL_PARAMLIST|0x0004|Вызов списка параметров метода.|  
|SCRIPT_CMPL_GLOBALLIST|0x0008|Глобальный список.|  
  
 Тип SCRIPT_CMPL_GLOBALLIST обрабатывается как элемент завершения по умолчанию, могут быть объединены с помощью оператора OR с другими элементами завершения. Скрипт создания engine сначала пытается получить информацию о типе для других элементы списков завершения заполнения. В случае неудачи ядро заполняет для SCRIPT_CMPL_GLOBALLIST.  
  
 `pdwListTypesProvided`  
 [out] Тип списка.  
  
 `pichListAnchorPosition`  
 [out] Начальный индекс, содержащий позицию текущего контекста. Начальный индекс отсчитывается относительно начала блока.  
  
 Заполняется, только если `dwListTypesRequested` включает SCRIPT_CMPL_MEMBERLIST, SCRIPT_CMPL_ENUMLIST или SCRIPT_CMPL_GLOBALLIST. Для других типов запрошенный список результат не определен.  
  
 `pichFuncAnchorPosition`  
 [out] Начальный индекс вызова функции, который содержит текущее положение. Начальный индекс отсчитывается относительно начала блока.  
  
 Заполняется только в том случае, когда контекст, содержащий текущую позицию, вызов функции и когда `dwListTypesRequested` включает SCRIPT_CMPL_PARAMLIST. В противном случае результат не определен.  
  
 `pmemid`  
 [out] MEMBERID в соответствии с определением типа в функции `IProvideMultipleClassInfo``ppunk` выходной параметр.  
  
 Заполняется, только если `dwListTypesRequested` включает SCRIPT_CMPL_PARAMLIST.  
  
 `piCurrentParameter`  
 [out] Индекс параметра, содержащего текущую позицию. Если текущее положение находится на имя функции, возвращается значение -1.  
  
 `piCurrentParameter` Значение заполняется, только если `dwListTypesRequested` включает SCRIPT_CMPL_PARAMLIST.  
  
 `ppunk`  
 Сведения о типе, который предоставляется в виде `IProvideMultipleClassInfo` объекта.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IProvideMultipleClassInfo](https://msdn.microsoft.com/library/microsoft.visualstudio.ole.interop.iprovidemultipleclassinfo.aspx)   
 [Интерфейс IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)