---
title: "IDiaSymbol::get_backEndMinor | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaSymbol::get_backEndMinor - метод"
ms.assetid: 37f38d19-6685-440d-a477-7127c4f8699e
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_backEndMinor
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Извлекает серверной части дополнительный номер версии компилятора.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT get_backEndMinor (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRetVal`  
 [out] Возвращает номер вспомогательной версии серверной части. См. заметки.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае — возвращает `S_FALSE` или код ошибки.  
  
> [!NOTE]
>  Возвращаемое значение `S_FALSE` означает, что свойство недоступно для символа.  
  
## <a name="remarks"></a>Примечания  
 Компилятор обычно состоят из двух основных элементов: внешнего интерфейса (средство синтаксического анализа), который обрабатывает анализа исходного кода в промежуточную форму, и серверной части (генератор кода), преобразующий промежуточную форму в сборку. Обычно не возникают для внешнего интерфейса использовать другую версию, чем серверной части.  
  
 Переднего плана или номер версии серверной части состоит из трех частей: \< основных>. \< дополнительный>. \< сборки>, где \< основных> номер основной версии \< вспомогательных> является дополнительный номер версии, и \< сборки> — номер сборки. Например, 13.10.3077.  
  
## <a name="requirements"></a>Требования  
  
|Требование|Описание|  
|-----------------|-----------------|  
|Заголовок:|dia2.h|  
|Версия:|ПАКЕТ SDK ДЛЯ версии 7.0|  
  
## <a name="see-also"></a>См. также  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)