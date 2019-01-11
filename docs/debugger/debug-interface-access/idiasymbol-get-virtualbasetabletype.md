---
title: IDiaSymbol::get_virtualBaseTableType | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_virtualBaseTableType method
ms.assetid: e0581c4f-0343-49b5-9754-a48477460e9f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 25e7361fd3a4b74aa04806de7001db3b4293a541
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53949671"
---
# <a name="idiasymbolgetvirtualbasetabletype"></a>IDiaSymbol::get_virtualBaseTableType
Извлекает тип указателя базовой виртуальной таблицы.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT get_virtualBaseTableType(  
   IDiaSymbol *pRetVal  
};  
```  
  
#### <a name="parameters"></a>Параметры  
  
|Параметр|Описание|  
|---------------|-----------------|  
|`pRetVal`|[out] Возвращает [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) , указывающий тип базовой таблицы.|  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.  
  
> [!NOTE]
>  Возвращаемое значение `S_FALSE` означает, что свойство недоступно для символа.  
  
## <a name="remarks"></a>Примечания  
 Указатель базовой виртуальной таблицы (`vbtptr`) — это скрытый указатель в [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] vtable, который обрабатывает наследование от виртуальных базовых классов. Объект `vbtptr` может иметь разные размеры в зависимости от наследуемые классы.  
  
 Этот метод возвращает [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) объект, который может использоваться для определения размера vbtptr.  
  
## <a name="requirements"></a>Требования  
  
|Требование|Описание|  
|-----------------|-----------------|  
|Заголовок:|dia2.h|  
|Версия:|ПАКЕТ SDK для версии 8.0|  
  
## <a name="see-also"></a>См. также раздел  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)