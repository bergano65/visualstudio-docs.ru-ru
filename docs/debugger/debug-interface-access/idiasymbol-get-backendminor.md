---
title: IDiaSymbol::get_backEndMinor | Документация Майкрософт
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
ms.openlocfilehash: a47287abb5230b44ebbdf0dcb300f6f386fccee4
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49925946"
---
# <a name="idiasymbolgetbackendminor"></a>IDiaSymbol::get_backEndMinor
Извлекает серверной части дополнительный номер версии компилятора.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT get_backEndMinor (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRetVal`  
 [out] Возвращает серверной части дополнительный номер версии. См. заметки.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.  
  
> [!NOTE]
>  Возвращаемое значение `S_FALSE` означает, что свойство недоступно для символа.  
  
## <a name="remarks"></a>Примечания  
 Компилятор обычно состоит из двух основных элементов: переднего плана (средство синтаксического анализа), который обрабатывает синтаксического анализа исходного кода в промежуточный форму, и серверной частью (генератор кода), который преобразует промежуточную форму в сборку. Нередко для внешнего интерфейса до имеют версию, отличную от серверной части.  
  
 Интерфейс или номер версии серверной части состоит из трех частей: \<основных >.\< дополнительный номер >. \<сборки >, где \<основных > — номер основной версии \<незначительные > — это дополнительный номер версии, и \<сборки > — номер сборки. Например, 13.10.3077.  
  
## <a name="requirements"></a>Требования  
  
|Требование|Описание|  
|-----------------|-----------------|  
|Заголовок:|dia2.h|  
|Версия:|ПАКЕТ SDK для версии 7.0|  
  
## <a name="see-also"></a>См. также  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)