---
redirect_url: shell/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file
title: "Изменение с помощью изолированной оболочки. Файл pkgundef-файлов | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Visual Studio shell, isolated mode, .pkgundef file
ms.assetid: 9cee2a20-f8ac-4d9d-aef9-068fcd9f27a4
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: dfe0e4b39e96d98718ff98025add521a678699ac
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="modifying-the-isolated-shell-by-using-the-pkgundef-file"></a>Изменение с помощью изолированной оболочки. Файл pkgundef-файлов
Можно изменить файл .pkgundef, чтобы исключить записи указанного раздела из приложения изолированной оболочки. Как правило при первом запуске приложения на компьютере, оболочка Visual Studio копирует существующие записи реестра Visual Studio корневого раздела реестра для приложения. Это включает в себя все ссылки на установленные пакеты VSPackage.  
  
 Чтобы исключить реестра из приложения isolated shell, добавьте в файл .pkgundef приложения, ключ пакета, а затем с помощью операции. Разделы и записи представлены как pkgdef-файл; то есть как [$RootKey$] или [$RootKey$\\*подраздел*] и»*запись*» =*значение*, где *подраздел* подраздел, чтобы внести изменения, *входа* является записи, которую требуется удалить, и *значение* либо `""` или `dword:00000000`.  
  
 Чтобы исключить несколько записей из раздела реестра, просто список ключ один раз, за которым следует строка для каждой записи исключить.  
  
 Чтобы исключить всего реестра из приложения isolated shell, добавить ключ в файле .pkgundef приложения, но не определяют записи в реестре для этого ключа.  
  
 Можно добавить комментарии к файлу .pkgundef. Однострочный комментарий должен иметь две косые черты, что первые два символа.  
  
 Например, чтобы удалить **подключение к базе данных** и **соединиться Serve r** команды **средства** меню можно раскомментируйте строку:  
  
```  
[$RootKey$\Packages\{8D8529D3-625D-4496-8354-3DAD630ECC1B}]  
```  
  
 и добавьте строку:  
  
```  
[$RootKey$\Packages\{198E76C1-34C0-424D-9957-B3EBD80265FB}]  
```  
  
 в файле .pkgundef приложения.  
  
## <a name="see-also"></a>См. также  
 [GUID пакета функций Visual Studio](../extensibility/package-guids-of-visual-studio-features.md)   
 [Настройка изолированной оболочки](../extensibility/customizing-the-isolated-shell.md)