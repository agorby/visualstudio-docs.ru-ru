---
title: Присоединение и отсоединение программы | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
- debug engines, detaching from programs
ms.assetid: 79dcbb9b-c7f8-40fc-8a00-f37fe1934f51
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ca1eab8c6b5e1edc2354ea5f2dfd8922bb7cae16
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="attaching-and-detaching-to-a-program"></a>Присоединение и отсоединение к программе
Подключение отладчика требуется отправить правильной последовательности, методов и событий с правильными атрибутами.  
  
## <a name="sequence-of-methods-and-events"></a>Последовательность методов и событий  
  
1.  Диспетчер сеансов отладки (SDM) вызывает [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) метод.  
  
     На основе модели процесса отладки ядра (DE), `IDebugProgramNodeAttach2::OnAttach` метод возвращает одно из следующих методов, которые определяет дальнейший ход событий.  
  
     Если `S_FALSE` возвращается, отладчик успешно подключен к программе. В противном случае [присоединение](../../extensibility/debugger/reference/idebugengine2-attach.md) метод вызывается для завершения процесса подключения.  
  
     Если `S_OK` возвращается, DE является должна быть загружена в том же процессе, что SDM. SDM выполняет следующие задачи:  
  
    1.  Вызовы [GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) для получения информация DE для поисковых систем.  
  
    2.  Совместно создает DE.  
  
    3.  Вызовы [присоединения](../../extensibility/debugger/reference/idebugengine2-attach.md).  
  
2.  Отправляет DE [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) для SDM с `EVENT_SYNC` атрибута.  
  
3.  Отправляет DE [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) для SDM с `EVENT_SYNC` атрибута.  
  
4.  Отправляет DE [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) для SDM с `EVENT_SYNC_STOP` атрибута.  
  
 Отсоединение от программы представлен простой, двухэтапный процесс.  
  
1.  Вызовы SDM [отсоединения](../../extensibility/debugger/reference/idebugprogram2-detach.md).  
  
2.  Отправляет DE [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md).  
  
## <a name="see-also"></a>См. также  
 [Вызов событий отладчика](../../extensibility/debugger/calling-debugger-events.md)