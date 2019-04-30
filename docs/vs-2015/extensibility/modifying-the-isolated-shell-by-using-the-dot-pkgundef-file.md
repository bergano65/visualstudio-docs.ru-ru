---
title: Изменение изолированной оболочки с помощью. Файл Pkgundef | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, isolated mode%2C .pkgundef file
ms.assetid: 9cee2a20-f8ac-4d9d-aef9-068fcd9f27a4
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: eab02fe900e96ba37c63faae535974788f99ba78
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62538398"
---
# <a name="modifying-the-isolated-shell-by-using-the-pkgundef-file"></a>Изменение изолированной оболочки с помощью. Файл Pkgundef
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Можно изменить файл .pkgundef, чтобы исключить записи указанного раздела из приложения изолированной оболочки. Как правило первый раз при запуске приложения на компьютере, оболочки Visual Studio копирует существующие записи реестра Visual Studio для корневого раздела реестра для приложения. Сюда входят все ссылки на установленные пакеты VSPackage.  
  
 Чтобы исключить реестра из приложений изолированной оболочки, добавьте файла .pkgundef приложения, ключа пакета, а затем с помощью записи. Разделы и записи представлены как в pkgdef-файл; то есть как [$RootKey$] или [$RootKey$\\*подраздел*] и "*запись*«=*значение*, где *подраздел* подраздел, чтобы внести изменения, *запись* — это записи, которую требуется удалить, и *значение* либо `""` или `dword:00000000`.  
  
 Чтобы исключить несколько записей из раздела реестра, а просто Перечислите ключ один раз, за которым следует строка для каждой записи, чтобы исключить.  
  
 Чтобы исключить всего реестра из приложений изолированной оболочки, добавить ключ в файле .pkgundef приложения, но не указывают записи в реестре для этого ключа.  
  
 Можно добавить комментарии к файлу .pkgundef. Однострочный комментарий должен иметь две косые черты, что первые два символа.  
  
 Например, чтобы удалить **подключение к базе данных** и **подключиться к Serve r** команд на **средства** меню можно раскомментируйте строку:  
  
```  
[$RootKey$\Packages\{8D8529D3-625D-4496-8354-3DAD630ECC1B}]  
```  
  
 и добавьте строку:  
  
```  
[$RootKey$\Packages\{198E76C1-34C0-424D-9957-B3EBD80265FB}]  
```  
  
 для файла .pkgundef приложения.  
  
## <a name="see-also"></a>См. также  
 [Пакет GUID функций Visual Studio](../extensibility/package-guids-of-visual-studio-features.md)   
 [Настройка изолированной оболочки](../extensibility/customizing-the-isolated-shell.md)
