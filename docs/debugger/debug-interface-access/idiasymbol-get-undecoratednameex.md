---
title: "IDiaSymbol::get_undecoratedNameEx | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSymbol::get_undecoratedNameEx method
ms.assetid: 579aed0b-c57d-41a1-a94a-3bf665fd4a9d
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1dac35a0e01890488e6290759b563d25f7067067
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idiasymbolgetundecoratednameex"></a>IDiaSymbol::get_undecoratedNameEx
Извлекает часть или все недекорированного имени для C++ внутреннего имени (связь).  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT get_undecoratedNameEx(   
   DWORD undecorateOptions,  
   BSTR* pRetval  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `undecoratedOptions`  
 [in] Включение управления возвращаемые сочетание флагов. В разделе примечаний для конкретных значений и их функции.  
  
 `pRetVal`  
 [out] Возвращает внешнее имя для C++ декорированного имени.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.  
  
> [!NOTE]
>  Возвращаемое значение `S_FALSE` означает свойство недоступно для символа.  
  
## <a name="remarks"></a>Примечания  
 `undecorateOptions` Может представлять собой сочетание следующих флагов.  
  
> [!NOTE]
>  Флаг имена не определены в пакет SDK для, вам нужно добавить объявления в код или использовать необработанные значения.  
  
|Flag|Значение|Описание|  
|----------|-----------|-----------------|  
|UNDNAME_COMPLETE|0x0000|Разрешает полный undecoration.|  
|UNDNAME_NO_LEADING_UNDERSCORES|0x0001|Удаляет начальные знаки подчеркивания из расширенные ключевые слова корпорации Майкрософт.|  
|UNDNAME_NO_MS_KEYWORDS|0x0002|Отключает расширения расширенные ключевые слова корпорации Майкрософт.|  
|UNDNAME_NO_FUNCTION_RETURNS|0x0004|Отключает расширения типа возвращаемого значения для основной объявления.|  
|UNDNAME_NO_ALLOCATION_MODEL|0x0008|Отключает расширения модели объявления.|  
|UNDNAME_NO_ALLOCATION_LANGUAGE|0x0010|Отключает расширения языка спецификатора объявления.|  
|UNDNAME_RESERVED1|0x0020|ЗАРЕЗЕРВИРОВАНО.|  
|UNDNAME_RESERVED2|0x0040|ЗАРЕЗЕРВИРОВАНО.|  
|UNDNAME_NO_THISTYPE|0x0060|Отключает все модификаторы для `this` типа.|  
|UNDNAME_NO_ACCESS_SPECIFIERS|0x0080|Отключает расширения описатели доступа для элементов.|  
|UNDNAME_NO_THROW_SIGNATURES|0x0100|Отключает расширения «throw-подписей» для функций и указатели на функции.|  
|UNDNAME_NO_MEMBER_TYPE|0x0200|Отключает расширения `static` или `virtual` члены.|  
|UNDNAME_NO_RETURN_UDT_MODEL|0x0400|Отключает расширения Microsoft модели для определяемого пользователем ТИПА возвращает.|  
|UNDNAME_32_BIT_DECODE|0x0800|Undecorates декорированные имена для 32-разрядной.|  
|UNDNAME_NAME_ONLY|0x1000|Возвращает только имя объявления источника; Возвращает только что [области::] имя.  При развертывании шаблона params.|  
|UNDNAME_TYPE_ONLY|0x2000|Входные данные имеет только тип кодирования; объединяет абстрактный декларатор.|  
|UNDNAME_HAVE_PARAMETERS|0x4000|Параметры шаблона реальные доступны.|  
|UNDNAME_NO_ECSU|0x8000|Подавляет enum, класса или структуры или объединения.|  
|UNDNAME_NO_IDENT_CHAR_CHECK|0x10000|Отключает проверку для допустимых символах.|  
|UNDNAME_NO_PTR64|0x20000|Не включайте ptr64 в выходных данных.|  
  
## <a name="see-also"></a>См. также  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)