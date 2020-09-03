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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196978"
---
# <a name="createexpinstance-utility"></a>Служебная программа CreateExpInstance
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Используйте служебную программу CreateExpInstance для создания, сброса или удаления экспериментального экземпляра Visual Studio. Экспериментальный экземпляр можно использовать для отладки и тестирования расширений Visual Studio без изменения базового продукта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
CreateExpInstance.exe [/Create | /Reset | /Clean] /VSInstance=VsInstance /RootSuffix=Suffix  
```  
  
#### <a name="parameters"></a>Параметры  
 /CREATE  
 Создает экспериментальный экземпляр.  
  
 /Reset  
 Удаляет экспериментальный экземпляр, а затем создает новый.  
  
 /Clean  
 Удаляет экспериментальный экземпляр.  
  
 /всинстанце  
 Имя каталога, содержащего базовый экземпляр Visual Studio для копирования.  
  
 /рутсуффикс  
 Суффикс, добавляемый к имени каталога экспериментального экземпляра.  
  
## <a name="remarks"></a>Remarks  
 При работе с расширением Visual Studio можно нажать клавишу F5, чтобы открыть экспериментальный экземпляр по умолчанию и установить текущее расширение. Если экспериментальный экземпляр недоступен, Visual Studio создает его с параметрами по умолчанию.  
  
 Расположение экспериментального экземпляра по умолчанию зависит от номера версии Visual Studio. Например, для Visual Studio 2015 расположение%localappdata%\Microsoft\VisualStudio\14.0Exp\ все файлы в расположении каталога считаются частью этого экземпляра. Все дополнительные экспериментальные экземпляры не будут загружаться Visual Studio, если только имя каталога не будет изменено на расположение по умолчанию.  
  
 Visual Studio не получает доступ к системному реестру при открытии экспериментального экземпляра. Это отличается от предыдущих версий Visual Studio, в которых использовалась экспериментальная версия куста реестра.  
  
 Служебная программа CreateExpInstance заменяет служебную программу Всрежекс.  
  
 В следующем примере выполняется сброс экспериментального экземпляра Visual Studio по умолчанию.  
  
 **CreateExpInstance.exe/Reset/Всинстанце = ~/Рутсуффикс = exp**  
  
## <a name="see-also"></a>См. также:  
 [Выпуск продукта](../../misc/releasing-a-visual-studio-integration-product.md)
