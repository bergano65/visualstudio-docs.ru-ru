---
title: -DebugExe (devenv.exe) | Документы Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Devenv, /DebugExe switch
- DebugExe switch
- /DebugExe [devenv.exe]
ms.assetid: cd700006-1648-418f-924b-4b1e5c1412ab
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 56ff98aa40e122b5067bd17d72334daf93164fe2
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49262656"
---
# <a name="debugexe-devenvexe"></a>/DebugExe (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Открывает указанный исполняемый файл для отладки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Devenv /debugexe ExecutableFile  
```  
  
## <a name="arguments"></a>Аргументы  
 `ExecutableFile`  
 Обязательно. Путь и имя EXE-файла.  
  
 Если EXE-файл не найден или не существует, никакие предупреждения или ошибки не выводятся, а [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] запускается обычным образом.  
  
## <a name="remarks"></a>Примечания  
 Строки, следующие за параметром `ExecutableFile`, передаются в этот файл в качестве аргументов.  
  
## <a name="example"></a>Пример  
 Следующий пример открывает файл `MyApplication.exe` для отладки.  
  
```  
Devenv.exe /debugexe MyApplication.exe  
```  
  
## <a name="see-also"></a>См. также  
 [Параметры командной строки для команды Devenv](../../ide/reference/devenv-command-line-switches.md)



