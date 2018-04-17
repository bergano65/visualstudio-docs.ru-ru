---
title: IDiaSymbol::get_frontEndMinor | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_frontEndMinor method
ms.assetid: 40792153-827c-4859-be7c-6aa16d5abab6
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2d0d7741d084a1adf8f7bdc7ac7c2e0f5e33cc72
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="idiasymbolgetfrontendminor"></a>IDiaSymbol::get_frontEndMinor
Извлекает интерфейс дополнительный номер версии.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT get_frontEndMinor (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRetVal`  
 [out] Возвращает front.end дополнительный номер версии.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.  
  
> [!NOTE]
>  Возвращаемое значение `S_FALSE` означает свойство недоступно для символа.  
  
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