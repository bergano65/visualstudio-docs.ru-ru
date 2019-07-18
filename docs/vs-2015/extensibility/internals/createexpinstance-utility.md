---
title: Служебная программа CreateExpInstance | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- experimental builds
- experimental hive
- experimental instance
- createexpinstance
- createexpinst
ms.assetid: 03779774-9401-49ae-997c-0c3ab25ed0d5
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7d778f0f31a7651412915a898bff9e4bdfe6c55f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68196978"
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
