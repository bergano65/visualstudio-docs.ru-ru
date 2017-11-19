---
title: "IDiaSymbol::get_frontEndMajor | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSymbol::get_frontEndMajor method
ms.assetid: f8a067c5-3306-4fc5-bc20-8910a47ed504
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1dad900b3009e5bd7117bbd7339fc41085b945ad
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idiasymbolgetfrontendmajor"></a>IDiaSymbol::get_frontEndMajor
Возвращает номер основной версии переднего плана.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT get_frontEndMajor (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRetVal`  
 [out] Возвращает номер основной версии переднего плана. См. заметки.  
  
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