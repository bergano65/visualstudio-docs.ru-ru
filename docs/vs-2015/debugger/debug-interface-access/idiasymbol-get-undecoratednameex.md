---
title: 'IDiaSymbol:: get_undecoratedNameEx | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_undecoratedNameEx method
ms.assetid: 579aed0b-c57d-41a1-a94a-3bf665fd4a9d
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f9c50f5d352d8a52b0eb8b125992b2c325e48234
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842892"
---
# <a name="idiasymbolget_undecoratednameex"></a>IDiaSymbol::get_undecoratedNameEx
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Извлекает часть или все недекорированное имя для декорированного имени C++ (компоновка).  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT get_undecoratedNameEx(   
   DWORD undecorateOptions,  
   BSTR* pRetval  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `undecoratedOptions`  
 окне Задает сочетание флагов, управляющих возвращаемым элементом. Конкретные значения и их действия см. в разделе "Примечания".  
  
 `pRetVal`  
 заполняет Возвращает недекорированное имя для декорированного имени C++.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK` ; в противном случае возвращает `S_FALSE` или код ошибки.  
  
> [!NOTE]
> Возвращаемое значение `S_FALSE` означает, что свойство недоступно для символа.  
  
## <a name="remarks"></a>Remarks  
 `undecorateOptions`Может быть сочетанием следующих флагов.  
  
> [!NOTE]
> Имена флагов не определены в пакете SDK для DIA, поэтому необходимо либо добавить объявления в код, либо использовать необработанные значения.  
  
|Флаг|Значение|Description|  
|----------|-----------|-----------------|  
|UNDNAME_COMPLETE|0x0000|Включает полное расоформление.|  
|UNDNAME_NO_LEADING_UNDERSCORES|0x0001|Удаляет начальные подчеркивания из расширенных ключевых слов Майкрософт.|  
|UNDNAME_NO_MS_KEYWORDS|0x0002|Отключает расширение ключевых слов Microsoft Extended.|  
|UNDNAME_NO_FUNCTION_RETURNS|0x0004|Отключает расширение типа возвращаемого значения для основного объявления.|  
|UNDNAME_NO_ALLOCATION_MODEL|0x0008|Отключает расширение модели объявления.|  
|UNDNAME_NO_ALLOCATION_LANGUAGE|0x0010|Отключает расширение описателя языка объявления.|  
|UNDNAME_RESERVED1|0x0020|ЗАРЕЗЕРВИРОВАНО.|  
|UNDNAME_RESERVED2|0x0040|ЗАРЕЗЕРВИРОВАНО.|  
|UNDNAME_NO_THISTYPE|0x0060|Отключает все модификаторы для `this` типа.|  
|UNDNAME_NO_ACCESS_SPECIFIERS|0x0080|Отключает расширение описателей доступа для членов.|  
|UNDNAME_NO_THROW_SIGNATURES|0x0100|Отключает расширение "Throw-Signatures" для функций и указателей на функции.|  
|UNDNAME_NO_MEMBER_TYPE|0x0200|Отключает расширение `static` элементов или `virtual` .|  
|UNDNAME_NO_RETURN_UDT_MODEL|0x0400|Отключает расширение модели Майкрософт для определяемых пользователем типов.|  
|UNDNAME_32_BIT_DECODE|0x0800|Раскрывающийся из 32-битных декорированных имен.|  
|UNDNAME_NAME_ONLY|0x1000|Возвращает только имя для основного объявления; Возвращает только [scope::] name.  Развертывает параметры шаблона.|  
|UNDNAME_TYPE_ONLY|0x2000|Входные данные — это просто Кодировка типов; формирует абстрактный декларатор.|  
|UNDNAME_HAVE_PARAMETERS|0x4000|Доступны реальные параметры шаблона.|  
|UNDNAME_NO_ECSU|0x8000|Подавляет перечисление, класс, структуру или объединение.|  
|UNDNAME_NO_IDENT_CHAR_CHECK|0x10000|Подавляет проверку допустимых символов идентификатора.|  
|UNDNAME_NO_PTR64|0x20000|Не включает ptr64 в выходные данные.|  
  
## <a name="see-also"></a>См. также:  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
