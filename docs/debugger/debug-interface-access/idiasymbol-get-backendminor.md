---
title: IDiaSymbol::get_backEndMinor | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_backEndMinor method
ms.assetid: 37f38d19-6685-440d-a477-7127c4f8699e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 292613903d30145f776654dbd3789894c5c3380b
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="idiasymbolgetbackendminor"></a>IDiaSymbol::get_backEndMinor
Извлекает внутренний дополнительный номер версии компилятора.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT get_backEndMinor (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRetVal`  
 [out] Возвращает внутренний дополнительный номер версии. См. заметки.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.  
  
> [!NOTE]
>  Возвращаемое значение `S_FALSE` означает, что свойство недоступно для символа.  
  
## <a name="remarks"></a>Примечания  
 Компилятор обычно состоит из двух основных элемента: внешнего интерфейса (средства синтаксического анализа), который обрабатывает разбора исходного кода в промежуточный формат, и серверную часть (генератор кода), который преобразует промежуточную форму в сборку. Довольно часто для внешнего интерфейса использовать другую версию, чем серверной части.  
  
 Интерфейс или внутренний номер версии состоит из трех частей: \<основной >.\< дополнительный номер >. \<сборки >, где \<основной > является основной номер версии, \<дополнительный > имеет дополнительный номер версии, и \<сборки > — номер сборки. Например, 13.10.3077.  
  
## <a name="requirements"></a>Требования  
  
|Требование|Описание|  
|-----------------|-----------------|  
|Заголовок:|dia2.h|  
|Версия:|ПАКЕТ SDK для v7.0|  
  
## <a name="see-also"></a>См. также  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)