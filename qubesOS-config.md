## QubesOS configuration

### GPU
#### &ensp; &ensp; Find out which of intel or fbdev driver is in use:
&ensp; &ensp; &ensp; &ensp; `grep -E 'LoadModule.*(fbdev|intel)"' /var/log/Xorg.0.log` <br/>
&ensp; &ensp; &ensp; &ensp; &ensp; &ensp; eg. for intel: <br/>
&ensp; &ensp; &ensp; &ensp; &ensp; &ensp; (II) LoadModule: "intel" <br/>

