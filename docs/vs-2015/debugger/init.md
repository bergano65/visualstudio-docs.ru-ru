---
title: Init | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c55ddec8-9101-4673-979b-4109caca9146
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a630906fa2a23a87853e8a835f155cda3ec06ecc
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49252399"
---
# <a name="init"></a>Init
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Подготавливает компонент диагностики графики в приложении к активному захвату и записи данных графики в файл журнала графики.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
void Init(  
  std::function<void (int len, wchar_t * pszBuffer)> vsgLogGetter  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `vsgLogGetter`  
 Вызываемая сущность — такая как функция, указатель на функцию, лямбда или объект-функция — которая принимает в качестве параметров длину буфера из `wchar_t` и указатель на этот буфер и возвращает `void`. При вызове эта вызываемая сущность определяет имя файла, который будет использоваться для записи сведений о графики, и записывает его в указанный буфер, прежде чем возвратить управление.  
  
## <a name="remarks"></a>Примечания  
 Функция `Init` вызывается автоматически при создании экземпляра класса `VsgDbg` путем установки параметра `bDefaultInit` его конструктора в значение `true`; в противном случае `Init` должна быть явным образом, прежде чем можно будет активно захватывать и записывать данные графики.  
  
 Вызвав `UnInit`, можно финализировать и закрыть активный файл журнала графики, а затем продолжить захват и запись других данных графики в новый файл журнала графики, снова вызвав `Init`. Это действие можно повторять сколько раз, сколько вы хотите создать независимых файлов журнала графики с использованием одного и того же экземпляра `VsgDbg`.  
  
## <a name="see-also"></a>См. также  
 [UnInit](../debugger/init.md)



