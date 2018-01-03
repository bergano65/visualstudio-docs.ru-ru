---
title: "-Out (devenv.exe) | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- errors [Visual Studio], builds
- Devenv, /out switch
- builds [Visual Studio], logs
- error logs [Visual Studio], command-line build errors
- error logs [Visual Studio]
- /out Devenv switch
- out Devenv switch
- builds [Visual Studio], errors
- output files, build errors
ms.assetid: 9002d8c2-36d4-451c-b489-8f01932f31f7
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 891204811a0c27471e8ab4be315da14be4b80794
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="out-devenvexe"></a>/Out (devenv.exe)
Задает файл для хранения и отображения ошибок при запуске, создании, перестроении или развертывании решения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
devenv /out FileName  
```  
  
## <a name="arguments"></a>Аргументы  
 `FileName`  
 Обязательно. Путь и имя файла для приема ошибок при сборке исполняемого файла.  
  
## <a name="remarks"></a>Примечания  
 Если указано несуществующее имя файла, такой файл создается автоматически. Если файл уже существует, то результаты добавляются к имеющемуся в нем содержимому.  
  
 Ошибки сборки в командной строке отображаются в окне **Команда** и представлении "Построитель решений" окна **Вывод**. Этот параметр полезен, если вы выполняете автоматические сборки и хотите видеть результаты.  
  
## <a name="example"></a>Пример  
 Этот пример запускает `MySolution` и записывает ошибки в файл `MyErrorLog.txt`.  
  
```  
devenv /run "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /out "C:\MyErrorLog.txt"  
```  
  
## <a name="see-also"></a>См. также  
 [Параметры командной строки для команды Devenv](../../ide/reference/devenv-command-line-switches.md)   
 [/Run (devenv.exe)](../../ide/reference/run-devenv-exe.md)   
 [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)   
 [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)   
 [/Deploy (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)