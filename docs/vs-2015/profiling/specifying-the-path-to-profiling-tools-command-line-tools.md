---
title: Указание пути к программам командной строки Средств профилирования | Документы Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7047bf18-5779-4f6e-872c-66e2fc47c969
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 886c035ddcc14b43200b13d789e59430cf090fdf
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51731271"
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



