---
title: XSLT-шаблоны по умолчанию | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 773dd34e-67d3-4997-8df9-b71e7f880d88
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 10937ed9c3ade13bf553ba4d3a2a9c551597949e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58993491"
---
# <a name="xslt-default-templates"></a>XSLT-шаблоны по умолчанию
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Если в таблице стилей отсутствует совпадающее явное правило шаблона, то во время обработки XSLT используется шаблон по умолчанию. Шаблон по умолчанию, называемый также встроенным правилом шаблона, определен в разделе  5.8 спецификации W3C XSLT 1.0. Шаблон по умолчанию разрешает обработчику XSLT обрабатывать узел, даже если ему не соответствует ни одно явное правило шаблона. Однако, поскольку встроенное правило шаблона явно не определено в таблице стилей, это может привести к непредвиденным или сбивающим с толку результатам XSLT-преобразования.  
  
 Отладчик XSLT теперь отображает код XSLT-шаблонов по умолчанию. При пошаговом выполнении XSLT-преобразования отладчик отображает в окне шаблон по умолчанию, если используется шаблон по умолчанию. Это позволяет выполнять по шагам код и задавать точки останова на инструкциях кода.  
  
## <a name="see-also"></a>См. также  
 [Отладка XSLT](../xml-tools/debugging-xslt.md)
