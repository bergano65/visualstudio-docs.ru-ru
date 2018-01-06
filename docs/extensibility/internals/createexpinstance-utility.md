---
title: "Программа CreateExpInstance | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- experimental builds
- experimental hive
- experimental instance
- createexpinstance
- createexpinst
ms.assetid: 03779774-9401-49ae-997c-0c3ab25ed0d5
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: c1104ebfbd066ad438262fcca0186acfb3854dbd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="createexpinstance-utility"></a>Программа CreateExpInstance
Используйте служебную программу CreateExpInstance для создания, сброс, или удалить экспериментальный экземпляр Visual Studio. Экспериментальный экземпляр можно использовать для отладки и тестирования расширений Visual Studio без изменения базового продукта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
CreateExpInstance.exe [/Create | /Reset | /Clean] /VSInstance=VsInstance /RootSuffix=Suffix  
```  
  
#### <a name="parameters"></a>Параметры  
 -Создание  
 Создает экспериментальный экземпляр.  
  
 / Reset  
 Удаляет экспериментальный экземпляр, а затем создает новый.  
  
 /Clean  
 Удаляет экспериментальный экземпляр.  
  
 / VSInstance  
 Имя каталога, содержащего базовый экземпляр Visual Studio для копирования.  
  
 / RootSuffix  
 Суффикс, добавляемый к имени каталога экспериментальный экземпляр.  
  
## <a name="remarks"></a>Примечания  
 При работе в расширение Visual Studio можно нажать F5, чтобы открыть экспериментальный экземпляр по умолчанию и установка текущего модуля. При наличии не экспериментальный экземпляр Visual Studio создает ту, которая имеет параметры по умолчанию.  
  
 Расположение по умолчанию экспериментального экземпляра зависит от номера версии Visual Studio. Например, расположение для Visual Studio 2015 — %localappdata%\Microsoft\VisualStudio\14.0Exp\ все файлы в каталоге, считаются частью этого экземпляра. Любые дополнительные экземпляры экспериментальный не будет загружен в Visual Studio до изменения имени каталога в папке по умолчанию.  
  
 Visual Studio не доступ к реестру системы при открытии экспериментальный экземпляр. Это отличается от более ранних версиях Visual Studio, которая используется версия экспериментальный куст реестра.  
  
 Программа CreateExpInstance заменяет программа VsRegEx.  
  
 В следующем примере сбрасывается в экспериментальном экземпляре Visual Studio по умолчанию.  
  
 **CreateExpInstance.exe/Reset / vsinstance = 14.0/rootsuffix = Exp**  
  
## <a name="see-also"></a>См. также  
 [Пакеты VSPackage](../../extensibility/internals/vspackages.md)