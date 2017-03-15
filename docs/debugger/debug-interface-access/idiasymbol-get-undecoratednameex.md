---
title: "IDiaSymbol::get_undecoratedNameEx | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaSymbol::get_undecoratedNameEx - метод"
ms.assetid: 579aed0b-c57d-41a1-a94a-3bf665fd4a9d
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# IDiaSymbol::get_undecoratedNameEx
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Возвращает часть или все упрощенного имени для C\+\+ украсили имя \(компоновки\).  
  
## Синтаксис  
  
```cpp#  
HRESULT get_undecoratedNameEx(   
   DWORD undecorateOptions,  
   BSTR* pRetval  
);  
```  
  
#### Параметры  
 `undecoratedOptions`  
 \[in\] сочетание указывает флаги, которые контролируют, что возвращаются.  См. раздел примeчаний для определенных значений и что они делают.  
  
 `pRetVal`  
 \[out\] возвращает упрощенного имя декорированного имени c C\+\+.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает  `S_FALSE` или код ошибки.  
  
> [!NOTE]
>  Возвращаемое значение  `S_FALSE` означает, что свойство недоступно для символа.  
  
## Заметки  
 `undecorateOptions` может быть сочетанием следующих флаги.  
  
> [!NOTE]
>  Имена пометить не указаны в пакет SDK для доступа к интерфейсу отладки, поэтому необходимо также добавить в код или объявления использовать исходные значения.  
  
|Flag|Значение|Описание|  
|----------|--------------|--------------|  
|UNDNAME\_COMPLETE|0x0000|Включает полный undecoration.|  
|UNDNAME\_NO\_LEADING\_UNDERSCORES|0x0001|Удаляет начальные символы подчеркивания из microsoft расширенные ключевые слова.|  
|UNDNAME\_NO\_MS\_KEYWORDS|0x0002|Запрещает расширение microsoft расширенные ключевые слова.|  
|UNDNAME\_NO\_FUNCTION\_RETURNS|0x0004|Запрещает расширение типа возвращаемого значения для первичного объявления.|  
|UNDNAME\_NO\_ALLOCATION\_MODEL|0x0008|Запрещает расширение модели объявления.|  
|UNDNAME\_NO\_ALLOCATION\_LANGUAGE|0x0010|Запрещает расширение описателя языка объявления.|  
|UNDNAME\_RESERVED1|0x0020|ЗАРЕЗЕРВИРОВАНО.|  
|UNDNAME\_RESERVED2|0x0040|ЗАРЕЗЕРВИРОВАНО.|  
|UNDNAME\_NO\_THISTYPE|0x0060|Запрещает все модификаторы на `this` этот тип.|  
|UNDNAME\_NO\_ACCESS\_SPECIFIERS|0x0080|Запрещает расширение описателей доступа для элементов.|  
|UNDNAME\_NO\_THROW\_SIGNATURES|0x0100|Запрещает расширение "ход\-подписей" для функций и указателей на функции.|  
|UNDNAME\_NO\_MEMBER\_TYPE|0x0200|Отключение расширения `static` OR  `virtual` члены.|  
|UNDNAME\_NO\_RETURN\_UDT\_MODEL|0x0400|Запрещает расширение модели Майкрософт для определяемых пользователем типов возвращаются.|  
|UNDNAME\_32\_BIT\_DECODE|0x0800|Декорированные имена Undecorates 32.|  
|UNDNAME\_NAME\_ONLY|0x1000|Возвращает только имя первичного объявления; возвращает просто:: \[region\] имя.  Разверните параметры шаблона.|  
|UNDNAME\_TYPE\_ONLY|0x2000|Вход как кодирование типа; представляет абстрактный декларатор.|  
|UNDNAME\_HAVE\_PARAMETERS|0x4000|Фактические параметры шаблона.|  
|UNDNAME\_NO\_ECSU|0x8000|Подавляет перечисления\/класс или структура или объединение.|  
|UNDNAME\_NO\_IDENT\_CHAR\_CHECK|0x10000|Отключает проверку для допустимых символов идентификатора.|  
|UNDNAME\_NO\_PTR64|0x20000|Не включает ptr64 на выходе.|  
  
## См. также  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)