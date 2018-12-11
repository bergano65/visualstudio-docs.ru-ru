---
title: Служебная программа CreateExpInstance | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- experimental builds
- experimental hive
- experimental instance
- createexpinstance
- createexpinst
ms.assetid: 03779774-9401-49ae-997c-0c3ab25ed0d5
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 73a6761e844cee41c1a6f0df79f0d6529f4a8215
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51768260"
---
# <a name="createexpinstance-utility"></a>Служебная программа CreateExpInstance
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Служебная программа CreateExpInstance для создания, сброс, или удалите экспериментальный экземпляр Visual Studio. Экспериментальный экземпляр можно использовать для отладки и тестирования расширений Visual Studio без изменения базовой продукта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
CreateExpInstance.exe [/Create | /Reset | /Clean] /VSInstance=VsInstance /RootSuffix=Suffix  
```  
  
#### <a name="parameters"></a>Параметры  
 Или создания  
 Создает экспериментальный экземпляр.  
  
 / Reset  
 Удаляет экспериментальный экземпляр, а затем создает новый.  
  
 /Clean  
 Удаляет экспериментальный экземпляр.  
  
 / VSInstance  
 Имя каталога, содержащего базовый экземпляр Visual Studio для копирования.  
  
 / RootSuffix  
 Суффикс для добавления к имени каталога экспериментальный экземпляр.  
  
## <a name="remarks"></a>Примечания  
 При работе в расширение Visual Studio, можно нажать F5, чтобы открыть экспериментальный экземпляр по умолчанию и установить текущего модуля. При наличии экспериментальный экземпляр Visual Studio создает один, который содержит настройки по умолчанию.  
  
 По умолчанию расположение экспериментального экземпляра зависит от номера версии Visual Studio. Например, Visual Studio 2015, расположен в расположении %localappdata%\Microsoft\VisualStudio\14.0Exp\ все файлы в каталоге, считаются частью этого экземпляра. Экспериментальные дополнительных экземпляров не будет загружен в Visual Studio до изменения имени каталога в расположение по умолчанию.  
  
 Visual Studio не осуществляет доступ к системного реестра при его открытии в экспериментальном экземпляре. Это отличается от более ранних версиях Visual Studio, в котором используется экспериментальная версия куст реестра.  
  
 Программа CreateExpInstance заменяет программа VsRegEx.  
  
 В следующем примере сбрасывается в экспериментальном экземпляре Visual Studio по умолчанию.  
  
 **/ Reset CreateExpInstance.exe /VSInstance = 14.0/rootsuffix = Exp**  
  
## <a name="see-also"></a>См. также  
 [Выпуск продукта](../../misc/releasing-a-visual-studio-integration-product.md)

