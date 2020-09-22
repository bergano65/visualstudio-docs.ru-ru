---
title: 'IDiaSymbol:: get_frontEndMinor | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_frontEndMinor method
ms.assetid: 40792153-827c-4859-be7c-6aa16d5abab6
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 12e5956f880a79d7946ff9655ec1ef3d1a79ff22
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842888"
---
# <a name="idiasymbolget_frontendminor"></a>IDiaSymbol::get_frontEndMinor
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Извлекает дополнительный номер версии внешнего интерфейса.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT get_frontEndMinor (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRetVal`  
 заполняет Возвращает номер промежуточной части переднего плана.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK` ; в противном случае возвращает `S_FALSE` или код ошибки.  
  
> [!NOTE]
> Возвращаемое значение `S_FALSE` означает, что свойство недоступно для символа.  
  
## <a name="remarks"></a>Remarks  
 Компилятор обычно состоит из двух основных элементов: внешнего интерфейса (средство синтаксического анализа), которое обрабатывает синтаксический анализ исходного кода в промежуточной форме и серверной части (генератор кода), который преобразует промежуточную форму в сборку. Нередко бывает, что внешний интерфейс имеет версию, отличную от версии серверной части.  
  
 Номер версии внешнего интерфейса или серверной части состоит из трех частей: \<major> . \<minor> . \<build> , где \<major> — основной номер версии, \<minor> — дополнительный номер версии, а \<build> — номер сборки. Например, 13.10.3077.  
  
## <a name="requirements"></a>Требования  
  
|Требование|Описание|  
|-----------------|-----------------|  
|Заголовок:|dia2. h|  
|Версия:|Пакет SDK для DIA версии 7.0|  
  
## <a name="see-also"></a>См. также:  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
