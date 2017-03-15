---
title: "Изменение с помощью изолированной оболочки. Файл Pkgundef | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, isolated mode, .pkgundef file
ms.assetid: 9cee2a20-f8ac-4d9d-aef9-068fcd9f27a4
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 9044821c2bfee0dba8ffa91f3d91afd565b8d957
ms.openlocfilehash: b49f3c5a39e82e0385aab12ef7042a6845b12664
ms.lasthandoff: 02/22/2017

---
# <a name="modifying-the-isolated-shell-by-using-the-pkgundef-file"></a>Изменение с помощью изолированной оболочки. Файл Pkgundef
Можно изменить файл .pkgundef, чтобы исключить записи реестра, указанный в приложении изолированной оболочки. Как правило при первом запуске приложения на компьютере, оболочка Visual Studio копирует существующие записи реестра Visual Studio корневого раздела реестра для приложения. Это включает все ссылки на установленные пакеты VSPackage.  
  
 Чтобы исключить реестра из приложения изолированной оболочки, добавьте в файл .pkgundef приложения, ключ пакета, а затем с помощью операции. Разделы и записи представляются как pkgdef-файл; то есть как [$RootKey$] или [$RootKey$\\*подраздел*] и»*запись*» =*значение*, где *подраздел* подраздел, чтобы внести изменения, *запись* является записи, которую требуется удалить, и *значение* либо `""` или `dword:00000000`.  
  
 Чтобы исключить несколько записей из реестра, просто список ключ один раз, за которым следует строка для каждой записи исключить.  
  
 Чтобы исключить всего реестра из приложения изолированной оболочки, добавить ключ в файле .pkgundef приложения, но не указывают записи в реестре для этого ключа.  
  
 Можно добавить комментарии к файлу .pkgundef. Однострочный комментарий должен иметь две косые черты, что первые два символа.  
  
 Например, чтобы удалить **подключение к базе данных** и **подключение к Serve r** команды на **средства** меню можно раскомментируйте строку:  
  
```  
[$RootKey$\Packages\{8D8529D3-625D-4496-8354-3DAD630ECC1B}]  
```  
  
 и добавьте строку:  
  
```  
[$RootKey$\Packages\{198E76C1-34C0-424D-9957-B3EBD80265FB}]  
```  
  
 в файле .pkgundef приложения.  
  
## <a name="see-also"></a>См. также  
 [GUID пакета возможностей Visual Studio](../extensibility/package-guids-of-visual-studio-features.md)   
 [Настройка изолированной оболочки](../extensibility/customizing-the-isolated-shell.md)
