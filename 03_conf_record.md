Archivos de grabacion 
ubicacion 
  /var/spool/asterisk/monitor
  
  
  Editar
    /etc/asterisk$ sudo vim extensions.conf
    descomentar la siguiente linea
    
    #include macros.conf
    
    :/etc/asterisk$ sudo vim macros.conf 


[macro-grabar]

exten => s,1,Set(fecha=${STRFTIME(${EPOCH},,%C%y)})

same => n,Set(mes=${STRFTIME(${EPOCH},,%m)})

same => n,Set(dia=${STRFTIME(${EPOCH},,%d)})

same => n,Set(calldir=/var/spool/asterisk/monitor/${fecha}/${mes}/${dia}/OUT)

same => n,Set(fecha=${STRFTIME(${EPOCH},,%C%y%m%d)})

same => n,MixMonitor(${calldir}/out-${ARG1}-${ARG5}-${fecha}-${hora}-${ARG4}.wav,av(0)V(0))

same => n,Set(CDR(userfield)=${calldir}/out-${ARG1}-${ARG5}-${fecha}-${hora}-${ARG4}.wav)
                                                            

Agregar en 

   :etc/asterisk$ sudo vim route_out.conf
   
 

exten => _10xx,1,NoOp(RUTA INTERNA extensiones)

exten => _10xx n,Macro(grabar,${EXTEN},${CDR(accountcode)},${CALLERID(num)},${UNIQUEID},${CHANNEL:6})

exten => _10xx,n,playback(tt-monkeys)

exten => _10xx,n,Hangup


AGREGAR 

  /etc/asterisk$ sudo vim extensions.conf 
  
include => int


Hacer esto

/etc/asterisk$ sudo vim route_out.conf


exten => _10XX,n,dial(SIP/${EXTEN}
;exten => _10XX,n,playback(tt-monkeys
