---
title: "Указание пути к программам командной строки Средств профилирования | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7047bf18-5779-4f6e-872c-66e2fc47c969
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: b33ee79d51dfcdb3db9021d3613672c44aef8956
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="specifying-the-path-to-profiling-tools-command-line-tools"></a>Указание пути к программам командной строки средств профилирования
Путь средств профилирования командной строки [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] не добавляется в переменную среды PATH. На 32-разрядных компьютерах эти средства находятся в одном каталоге. Существуют 64- и 32-разрядные версии средств профилирования для 64-разрядных компьютеров.  
  
## <a name="32-bit-computers"></a>32-разрядные компьютеры  
 На 32-разрядных компьютерах каталог Средств профилирования по умолчанию — *диск*\Program Files\Microsoft Visual Studio 11.0\Team Tools\Performance Tools.  
  
## <a name="64-bit-computers"></a>64-разрядные компьютеры  
 На 64-разрядных компьютерах укажите путь в соответствии с целевой платформой профилируемого приложения.  
  
-   Для 32-разрядных приложений каталог средств профилирования по умолчанию:  
  
     *диск*\Program Files (x86)\Microsoft Visual Studio 11.0\Team Tools\Performance Tools  
  
-   Для 64-разрядных приложений каталог средств профилирования по умолчанию:  
  
     *диск*\Program Files (x86)\Microsoft Visual Studio 11.0\Team Tools\Performance Tools\x64