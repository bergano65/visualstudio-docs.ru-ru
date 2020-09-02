---
title: 'IDiaSymbol:: get_editAndContinueEnabled | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_editAndContinueEnabled method
ms.assetid: cd703c64-9ff8-4654-8493-8cde9309cb22
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 74ac007a3b9d42677c77989ea36c6e20f9cd35f7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697717"
---
# <a name="idiasymbolget_editandcontinueenabled"></a>IDiaSymbol::get_editAndContinueEnabled
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Получает флаг, указывающий, был ли модуль скомпилирован с параметром компилятора [/Z7,/Zi,/Zi (формат отладочной информации)](https://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8) .  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT get_editAndContinueEnabled (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRetVal`  
 заполняет Возвращает значение `TRUE` , если функция Edit-and-Continue была включена во время компиляции. в противном случае возвращает `FALSE` .  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK` ; в противном случае возвращает `S_FALSE` или код ошибки.  
  
> [!NOTE]
> Возвращаемое значение `S_FALSE` означает, что свойство недоступно для символа.  
  
## <a name="requirements"></a>Требования  
  
|Требование|Описание|  
|-----------------|-----------------|  
|Заголовок:|dia2. h|  
|Версия:|Пакет SDK для DIA версии 7.0|  
  
## <a name="see-also"></a>См. также:  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [/Z7,/Zi,/ZI (формат отладочной информации)](https://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8)
