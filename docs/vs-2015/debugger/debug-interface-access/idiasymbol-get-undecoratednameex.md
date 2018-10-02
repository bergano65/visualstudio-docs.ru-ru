---
title: IDiaSymbol::get_undecoratedNameEx | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_undecoratedNameEx method
ms.assetid: 579aed0b-c57d-41a1-a94a-3bf665fd4a9d
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e8299775b1cb75a874c4d79de9560d7149bb36d4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47564173"
---
# <a name="idiasymbolgetundecoratednameex"></a>IDiaSymbol::get_undecoratedNameEx
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDiaSymbol::get_undecoratedNameEx](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiasymbol-get-undecoratednameex).  
  
Извлекает часть или вся недекорированное имя для C++ внутреннее имя (компоновка).  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT get_undecoratedNameEx(   
   DWORD undecorateOptions,  
   BSTR* pRetval  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `undecoratedOptions`  
 [in] Включение управления, что возвращается сочетание флагов. См. в разделе "Примечания" конкретные значения, и что они делают.  
  
 `pRetVal`  
 [out] Возвращает внешнее имя для C++ декорированное имя.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.  
  
> [!NOTE]
>  Возвращаемое значение `S_FALSE` означает, что свойство недоступно для символа.  
  
## <a name="remarks"></a>Примечания  
 `undecorateOptions` Может представлять собой сочетание следующих флагов.  
  
> [!NOTE]
>  Помечать имена не определены в пакете SDK для доступа к интерфейсу отладки, поэтому вам нужно добавить объявления в код или использовать необработанные значения.  
  
|Flag|Значение|Описание|  
|----------|-----------|-----------------|  
|UNDNAME_COMPLETE|0x0000|Включает полное undecoration.|  
|UNDNAME_NO_LEADING_UNDERSCORES|0x0001|Удаляет начальные символы подчеркивания от корпорации Майкрософт расширить ключевые слова.|  
|UNDNAME_NO_MS_KEYWORDS|0x0002|Отключает расширения Microsoft расширенных ключевые слова.|  
|UNDNAME_NO_FUNCTION_RETURNS|0x0004|Отключает расширения типа возвращаемого значения для основного объявления.|  
|UNDNAME_NO_ALLOCATION_MODEL|0x0008|Отключает расширения модели объявления.|  
|UNDNAME_NO_ALLOCATION_LANGUAGE|0x0010|Отключает расширения языка спецификатора объявления.|  
|UNDNAME_RESERVED1|0x0020|ЗАРЕЗЕРВИРОВАНО.|  
|UNDNAME_RESERVED2|0x0040|ЗАРЕЗЕРВИРОВАНО.|  
|UNDNAME_NO_THISTYPE|0x0060|Отключает все модификаторы на `this` типа.|  
|UNDNAME_NO_ACCESS_SPECIFIERS|0x0080|Отключает расширения описатели доступа для участников.|  
|UNDNAME_NO_THROW_SIGNATURES|0x0100|Отключает расширения из throw — «сигнатур» для функций и указателей на функции.|  
|UNDNAME_NO_MEMBER_TYPE|0x0200|Отключает расширения `static` или `virtual` членов.|  
|UNDNAME_NO_RETURN_UDT_MODEL|0x0400|Отключает расширения Microsoft модели для определяемого пользователем ТИПА возвращает.|  
|UNDNAME_32_BIT_DECODE|0x0800|Undecorates декорированные имена в 32-разрядной.|  
|UNDNAME_NAME_ONLY|0x1000|Возвращает только имя для основного объявление; Возвращает только [области::] имя.  При развертывании шаблона params.|  
|UNDNAME_TYPE_ONLY|0x2000|Входные данные — это просто тип кодирования; выполняет композицию абстрактный декларатор.|  
|UNDNAME_HAVE_PARAMETERS|0x4000|Доступны параметры реальных шаблона.|  
|UNDNAME_NO_ECSU|0x8000|Подавляет enum/классом, структурой или объединением.|  
|UNDNAME_NO_IDENT_CHAR_CHECK|0x10000|Отключает проверку для допустимых символах идентификаторов.|  
|UNDNAME_NO_PTR64|0x20000|Не включает ptr64 в выходных данных.|  
  
## <a name="see-also"></a>См. также  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



