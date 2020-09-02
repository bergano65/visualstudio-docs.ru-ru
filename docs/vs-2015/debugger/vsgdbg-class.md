---
title: Класс VsgDbg | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 6722263c-ccef-40c7-a0ae-87a863fbab00
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 053647d48324f056148375bae9268b997ba8721f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68145696"
---
# <a name="vsgdbg-class"></a>Класс VsgDbg
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Интерфейс для программного управления компонентом диагностики графики в приложении.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
class VsgDbg;  
```  
  
## <a name="members"></a>Участники  
 Класс `VsgDbg` поддерживает указанные ниже элементы.  
  
### <a name="public-constructors"></a>Открытые конструкторы  
  
|name|Описание|  
|----------|-----------------|  
|[VsgDbg::VsgDbg (конструктор)](../debugger/vsgdbg-vsgdbg-constructor.md)|Создает экземпляр класса `VsgDbg` и, если нужно, подготавливает компонент диагностики графики в приложении к активному захвату и записи данных графики.|  
|[VsgDbg::~VsgDbg (деструктор)](../debugger/vsgdbg-tilde-vsgdbg-destructor.md)|Уничтожает экземпляр класса `VsgDbg`.|  
  
### <a name="public-methods"></a>Открытые методы  
  
|name|Описание|  
|----------|-----------------|  
|[AddMessage](../debugger/addmessage.md)|Добавляет пользовательское сообщение на головной дисплей (HUD) диагностики графики.|  
|[BeginCapture](../debugger/begincapture.md)|Начинает интервал захвата, завершенный функцией `EndCapture`.|  
|[CaptureCurrentFrame](../debugger/capturecurrentframe.md)|Захватывает оставшуюся часть текущего кадра в файл журнала графики.|  
|[Copy (программный захват)](../debugger/copy-programmatic-capture.md)|Копирует содержимое активного файла журнала графики (.vsglog) в новый файл.|  
|[EndCapture](../debugger/endcapture.md)|Завершает интервал захвата, начатый функцией `BeginCapture`.|  
|[Init](../debugger/init.md)|Подготавливает компонент диагностики графики в приложении к активному захвату и записи данных графики.|  
|[ToggleHUD](../debugger/togglehud.md)|Включает или выключает наложение HUD диагностики графики.|  
|[UnInit](../debugger/uninit.md)|Финализирует файл журнала графики, закрывает его и освобождает все ресурсы, которые использовались во время активной записи данных графики приложением.|  
  
## <a name="remarks"></a>Примечания  
 Класс `VsgDbg` представляет интерфейс, который можно использовать для программного управления функциями диагностики графики. Некоторые функции можно использовать даже в том случае, если активный захват и запись графических данных не выполняются. В их число входят функция-член `AddMessage` и функция-член `ToggleHUD`. Другие функции-члены либо подготавливают компонент диагностики графики в приложении для запуска или завершения активного захвата и записи данных графики, либо должны вызываться, пока приложение активно захватывает и записывает данные графики в файл журнала графики.
