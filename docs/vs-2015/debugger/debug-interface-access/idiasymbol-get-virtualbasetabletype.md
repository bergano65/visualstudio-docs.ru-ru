---
title: IDiaSymbol::get_virtualBaseTableType | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
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
- IDiaSymbol::get_virtualBaseTableType method
ms.assetid: e0581c4f-0343-49b5-9754-a48477460e9f
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4e72d034b05c7777be536722ba6ed624122fb569
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49827302"
---
# <a name="idiasymbolgetvirtualbasetabletype"></a>IDiaSymbol::get_virtualBaseTableType
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Извлекает тип указателя базовой виртуальной таблицы.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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
 Указатель базовой виртуальной таблицы (`vbtptr`) — это скрытый указатель в [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] vtable, который обрабатывает наследование от виртуальных базовых классов. Объект `vbtptr` может иметь разные размеры в зависимости от наследуемые классы.  
  
 Этот метод возвращает [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) объект, который может использоваться для определения размера vbtptr.  
  
## <a name="requirements"></a>Требования  
  
|Требование|Описание|  
|-----------------|-----------------|  
|Заголовок:|dia2.h|  
|Версия:|ПАКЕТ SDK для версии 8.0|  
  
## <a name="see-also"></a>См. также  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



