---
title: IDiaSymbol::get_isDataAligned | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isDataAligned method
ms.assetid: ddd11a41-6c00-4829-acf4-aa1ace8c21a7
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d4c2d43129eadb0b0779086fc5dba0860c735cac
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49837806"
---
# <a name="idiasymbolgetisdataaligned"></a>IDiaSymbol::get_isDataAligned
Получает флаг, указывающий, выровнены ли определяемый пользователем тип (UDT) для некоторых границ памяти.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT get_isDataAligned(  
   BOOL *pFlag  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pFlag`  
 [out] Возвращает `TRUE` Если определяемый пользователем тип был выровнен по границе некоторых памяти; в противном случае возвращает `FALSE`.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.  
  
> [!NOTE]
>  Возвращаемое значение `S_FALSE` означает, что свойство недоступно для символа.  
  
## <a name="remarks"></a>Примечания  
 Как правило, это свойство имеет значение, когда исполняемый файл компилируется с выравниванием данных не по умолчанию. Например, компилятор Microsoft C++ можно изменить выравнивание данных с параметром командной строки/Zp<em>#</em>, где *#* является байтовым значением.  
  
## <a name="requirements"></a>Требования  
  
|Требование|Описание|  
|-----------------|-----------------|  
|Заголовок:|dia2.h|  
|Версия:|ПАКЕТ SDK для версии 8.0|  
  
## <a name="see-also"></a>См. также  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)