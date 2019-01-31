---
title: Указание пути к программам командной строки Средств профилирования | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 7047bf18-5779-4f6e-872c-66e2fc47c969
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 209c2263e35bc4e6c5bfffb03b4a760e8cc15a45
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "54791756"
---
# <a name="specifying-the-path-to-profiling-tools-command-line-tools"></a>Указание пути к программам командной строки средств профилирования
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Путь средств профилирования командной строки [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] не добавляется в переменную среды PATH. На 32-разрядных компьютерах эти средства находятся в одном каталоге. Существуют 64- и 32-разрядные версии средств профилирования для 64-разрядных компьютеров.  
  
## <a name="32-bit-computers"></a>32-разрядные компьютеры  
 На 32-разрядных компьютерах каталог Средств профилирования по умолчанию — *диск*\Program Files\Microsoft Visual Studio 11.0\Team Tools\Performance Tools.  
  
## <a name="64-bit-computers"></a>64-разрядные компьютеры  
 На 64-разрядных компьютерах укажите путь в соответствии с целевой платформой профилируемого приложения.  
  
-   Для 32-разрядных приложений каталог средств профилирования по умолчанию:  
  
     *диск*\Program Files (x86)\Microsoft Visual Studio 11.0\Team Tools\Performance Tools  
  
-   Для 64-разрядных приложений каталог средств профилирования по умолчанию:  
  
     *диск*\Program Files (x86)\Microsoft Visual Studio 11.0\Team Tools\Performance Tools\x64
