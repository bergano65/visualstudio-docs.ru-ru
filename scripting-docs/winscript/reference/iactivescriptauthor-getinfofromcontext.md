---
title: IActiveScriptAuthor::GetInfoFromContext | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetInfoFromContext
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetInfoFromContext
ms.assetid: 9891b095-6eb5-4473-87c0-c2e5cd2afc1a
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2d32e2864f42fa9a2bfc30cfe83da7d4e021dfd0
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54088872"
---
# <a name="iactivescriptauthorgetinfofromcontext"></a>IActiveScriptAuthor::GetInfoFromContext
Возвращает тип сведений и положения привязки для заданного символа в блоке кода. Это предоставляет сведения для элемента, IntelliSense, глобальные списки и подсказки по параметрам.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
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
 [in] Адрес строки блока кода, используемый для формирования результатов сведения.  
  
 `cchCode`  
 [in] Длина блока кода.  
  
 `ichCurrentPosition`  
 [in] Положение символа относительно начала блока.  
  
 `dwListTypesRequested`  
 [in] Типы списков, в запросе. Может быть сочетанием следующих значений:  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|SCRIPT_CMPL_NOLIST|0x0000|Список отсутствует.|  
|SCRIPT_CMPL_MEMBERLIST|0x0001|Список членов.|  
|SCRIPT_CMPL_ENUMLIST|0x0002|Список перечисления.|  
|SCRIPT_CMPL_PARAMLIST|0x0004|Вызов списка параметров метода.|  
|SCRIPT_CMPL_GLOBALLIST|0x0008|Глобальный список.|  
  
 Тип SCRIPT_CMPL_GLOBALLIST обрабатывается как элемент завершения по умолчанию, которые могут быть объединены с помощью оператора OR с другими элементами завершения. Скрипт создания ядра сначала пытается заполнить сведения о типе для других элементов списка завершения. В случае неудачи для SCRIPT_CMPL_GLOBALLIST заполняет ядро.  
  
 `pdwListTypesProvided`  
 [out] Тип списка.  
  
 `pichListAnchorPosition`  
 [out] Начальный индекс контекст, содержащий текущую позицию. Начальный индекс отсчитывается от начала блока.  
  
 Это поле заполняется только тогда, когда `dwListTypesRequested` включает в себя SCRIPT_CMPL_MEMBERLIST, SCRIPT_CMPL_ENUMLIST или SCRIPT_CMPL_GLOBALLIST. Для других типов запрошенный список результат не определен.  
  
 `pichFuncAnchorPosition`  
 [out] Начальный индекс вызов функции, которая содержит текущую позицию. Начальный индекс отсчитывается от начала блока.  
  
 Это поле заполняется только в том случае, когда контекст, содержащий текущее положение является вызовом функции и когда `dwListTypesRequested` включает SCRIPT_CMPL_PARAMLIST. В противном случае результат не определен.  
  
 `pmemid`  
 [out] Идентификатор функции, как определяется типом в `IProvideMultipleClassInfo``ppunk` выходной параметр.  
  
 Это поле заполняется только тогда, когда `dwListTypesRequested` включает SCRIPT_CMPL_PARAMLIST.  
  
 `piCurrentParameter`  
 [out] Индекс параметра, содержащего текущую позицию. Если текущая позиция находится на имя функции, возвращается значение -1.  
  
 `piCurrentParameter` Значение заполняется только тогда, когда `dwListTypesRequested` включает SCRIPT_CMPL_PARAMLIST.  
  
 `ppunk`  
 Сведения о типе, который предоставляется в виде `IProvideMultipleClassInfo` объекта.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IProvideMultipleClassInfo](https://docs.microsoft.com/dotnet/api/microsoft.visualstudio.ole.interop.iprovidemultipleclassinfo)   
 [Интерфейс IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)