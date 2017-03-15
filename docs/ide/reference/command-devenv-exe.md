---
title: "-Command (devenv.exe) | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Devenv, /command switch
- /command Devenv switch
ms.assetid: 13c20cd6-f09d-400a-8b7b-ecc266a32cef
caps.latest.revision: 11
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
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
translationtype: Human Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 76e64002e7f9caf7db8511501dd6c320b237ca65
ms.lasthandoff: 02/22/2017

---
# <a name="command-devenvexe"></a>/Command (devenv.exe)
Выполняет заданную команду после запуска интегрированной среды разработки (IDE) [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  
```  
devenv /command CommandName  
```  
  
## <a name="arguments"></a>Аргументы  
 `CommandName`  
 Обязательный. Полное имя команды [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] или ее псевдоним, заключенные в двойные кавычки. Дополнительные сведения о синтаксисе команд и псевдонимов см. в разделе [Команды Visual Studio](../../ide/reference/visual-studio-commands.md).  
  
## <a name="remarks"></a>Примечания  
 После завершения запуска интегрированная среда разработки выполняет именованную команду. При использовании этого параметра среда IDE не отображает начальную страницу [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] при запуске.  
  
 Если надстройка предоставляет команду, этот параметр можно использовать для запуска надстройки из командной строки. Дополнительные сведения см. в разделе [Практическое руководство. Управление надстройками с помощью диспетчера надстроек](http://msdn.microsoft.com/Library/4f60444a-cb48-4cdb-8df4-941f6419aeeb).  
  
## <a name="example"></a>Пример  
 В данном примере запускается [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] и автоматически выполняется макрос Open Favorite Files.  
  
```  
devenv /command "Macros.MyMacros.Module1.OpenFavoriteFiles"  
```  
  
## <a name="see-also"></a>См. также  
 [Параметры командной строки для команды Devenv](../../ide/reference/devenv-command-line-switches.md)   
 [Псевдонимы команд Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
