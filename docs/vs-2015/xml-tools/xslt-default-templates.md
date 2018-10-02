---
title: XSLT-шаблоны по умолчанию | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 773dd34e-67d3-4997-8df9-b71e7f880d88
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e5ddc4765ee8e2efe7dc8842abdb071a2fd37057
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47571293"
---
# <a name="xslt-default-templates"></a>XSLT-шаблоны по умолчанию
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Если в таблице стилей отсутствует совпадающее явное правило шаблона, то во время обработки XSLT используется шаблон по умолчанию. Шаблон по умолчанию, называемый также встроенным правилом шаблона, определен в разделе  5.8 спецификации W3C XSLT 1.0. Шаблон по умолчанию разрешает обработчику XSLT обрабатывать узел, даже если ему не соответствует ни одно явное правило шаблона. Однако, поскольку встроенное правило шаблона явно не определено в таблице стилей, это может привести к непредвиденным или сбивающим с толку результатам XSLT-преобразования.  
  
 Отладчик XSLT теперь отображает код XSLT-шаблонов по умолчанию. При пошаговом выполнении XSLT-преобразования отладчик отображает в окне шаблон по умолчанию, если используется шаблон по умолчанию. Это позволяет выполнять по шагам код и задавать точки останова на инструкциях кода.  
  
## <a name="see-also"></a>См. также  
 [Отладка XSLT](../xml-tools/debugging-xslt.md)

