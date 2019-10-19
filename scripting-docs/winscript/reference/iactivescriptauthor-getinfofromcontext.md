---
title: 'Иактивескриптаусор:: Жетинфофромконтекст | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 457b2ad1bda3226caf3604e3ccd6b976f01bca83
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576211"
---
# <a name="iactivescriptauthorgetinfofromcontext"></a>IActiveScriptAuthor::GetInfoFromContext
Возвращает сведения о типе и позиции привязки для заданного символа в блоке кода. Это предоставляет сведения для элементов IntelliSense, глобальных списков и советов по параметрам.  
  
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
 окне Адрес строки блока кода, используемой для создания результатов информации.  
  
 `cchCode`  
 окне Длина блока кода.  
  
 `ichCurrentPosition`  
 окне Расположение символа относительно начала блока.  
  
 `dwListTypesRequested`  
 окне Запрошенные типы списков. Может быть сочетанием следующих значений:  
  
|Константа|значения|Описание|  
|--------------|-----------|-----------------|  
|SCRIPT_CMPL_NOLIST|0x0000|Нет списка.|  
|SCRIPT_CMPL_MEMBERLIST|0x0001|Список членов.|  
|SCRIPT_CMPL_ENUMLIST|0x0002|Список перечислений.|  
|SCRIPT_CMPL_PARAMLIST|0x0004|Список параметров метода вызова.|  
|SCRIPT_CMPL_GLOBALLIST|0x0008|Глобальный список.|  
  
 Тип SCRIPT_CMPL_GLOBALLIST обрабатывается как элемент завершения по умолчанию, который можно объединить с помощью оператора или с другими элементами завершения. Обработчик создания скриптов сначала пытается заполнить сведения о типе для других элементов списка завершения. Если это не удается, подсистема заполняет SCRIPT_CMPL_GLOBALLIST.  
  
 `pdwListTypesProvided`  
 заполняет Тип предоставленного списка.  
  
 `pichListAnchorPosition`  
 заполняет Начальный индекс контекста, содержащего текущую позиции. Начальный индекс задается относительно начала блока.  
  
 Заполняется только в том случае, если `dwListTypesRequested` включает SCRIPT_CMPL_MEMBERLIST, SCRIPT_CMPL_ENUMLIST или SCRIPT_CMPL_GLOBALLIST. Для других запрошенных типов списков результат не определен.  
  
 `pichFuncAnchorPosition`  
 заполняет Начальный индекс вызова функции, который содержит текущую позиции. Начальный индекс задается относительно начала блока.  
  
 Заполняется только в том случае, если контекст, содержащий текущую точку, является вызовом функции и когда `dwListTypesRequested` включает SCRIPT_CMPL_PARAMLIST. В противном случае результат не определен.  
  
 `pmemid`  
 заполняет MEMBERID функции, как определено типом в параметре `IProvideMultipleClassInfo``ppunk` out.  
  
 Заполняется только в том случае, если `dwListTypesRequested` включает SCRIPT_CMPL_PARAMLIST.  
  
 `piCurrentParameter`  
 заполняет Индекс параметра, содержащего текущую позиции. Если текущей позицией является имя функции, возвращается значение-1.  
  
 Значение `piCurrentParameter` заполняется только в том случае, если `dwListTypesRequested` включает SCRIPT_CMPL_PARAMLIST.  
  
 `ppunk`  
 Сведения о типе, которые предоставляются в виде объекта `IProvideMultipleClassInfo`.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|значения|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Заметки  
  
## <a name="see-also"></a>См. также  
 @No__t_1 [интерфейса ипровидемултиплеклассинфо](https://docs.microsoft.com/dotnet/api/microsoft.visualstudio.ole.interop.iprovidemultipleclassinfo)  
 [Интерфейс IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)