---
title: Измерение | Документация Майкрософт
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
- Dimension Symbol
ms.assetid: 94f791da-bfea-454f-8a14-da31e8e1596a
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 854db8bc8d51284c4a6ea75e7091f1fa8dabdd28
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51790946"
---
# <a name="dimension"></a>Измерение
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Каждый массив FORTRAN имеет измерения, который определяется параметром `SymTagDimension` символов.  
  
## <a name="properties"></a>Свойства  
 Ниже приведены дополнительные допустимые свойства для данного типа символов.  
  
|Свойство.|Тип данных|Описание:|  
|--------------|---------------|-----------------|  
|[IDiaSymbol::get_lowerBound](../../debugger/debug-interface-access/idiasymbol-get-lowerbound.md)|`IDiaSymbol*`|Нижняя граница массива измерения FORTRAN.|  
|[IDiaSymbol::get_lowerBoundId](../../debugger/debug-interface-access/idiasymbol-get-lowerboundid.md)|`DWORD`|Идентификатор символа, нижняя граница.|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Идентификатор индекса символа.|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Возвращает `SymTagDimension` (один из [перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) значения).|  
|[IDiaSymbol::get_upperBound](../../debugger/debug-interface-access/idiasymbol-get-upperbound.md)|`IDiaSymbol*`|Верхняя граница FORTRAN измерения массива.|  
|[IDiaSymbol::get_upperBoundId](../../debugger/debug-interface-access/idiasymbol-get-upperboundid.md)|`DWORD`|Идентификатор верхней границы символа.|  
  
## <a name="see-also"></a>См. также  
 [ArrayType](../../debugger/debug-interface-access/arraytype.md)   
 [Иерархия классов символьных типов](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)



