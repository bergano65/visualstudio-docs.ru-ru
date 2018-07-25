---
title: Указание пути к программам командной строки Средств профилирования | Документы Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 7047bf18-5779-4f6e-872c-66e2fc47c969
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1afb0b00a7e121c611dedbc235684a67cc9cec53
ms.sourcegitcommit: 1b9c1e333c2f096d35cfc77e846116f8e5054557
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/06/2018
ms.locfileid: "34814499"
---
# <a name="specify-the-path-to-profiling-tools-command-line-tools"></a>Указание пути к программам командной строки средств профилирования
Путь средств профилирования командной строки [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] не добавляется в переменную среды PATH. На 32-разрядных компьютерах эти средства находятся в одном каталоге. Существуют 64- и 32-разрядные версии средств профилирования для 64-разрядных компьютеров.  
  
## <a name="32-bit-computers"></a>32-разрядные компьютеры  
 На 32-разрядных компьютерах каталог Средств профилирования по умолчанию — *диск\Program Files\Microsoft Visual Studio 11.0\Team Tools\Performance Tools*.  
  
## <a name="64-bit-computers"></a>64-разрядные компьютеры  
 На 64-разрядных компьютерах укажите путь в соответствии с целевой платформой профилируемого приложения.  
  
-   Для 32-разрядных приложений каталог средств профилирования по умолчанию:  
  
     *диск\Program Files (x86)\Microsoft Visual Studio 11.0\Team Tools\Performance Tools*  
  
-   Для 64-разрядных приложений каталог средств профилирования по умолчанию:  
  
     *диск\Program Files (x86)\Microsoft Visual Studio 11.0\Team Tools\Performance Tools\x64*