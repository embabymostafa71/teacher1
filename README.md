[teacher.html](https://github.com/user-attachments/files/35395704/teacher.html)
<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Teacher — Gemini</title>
<style>
:root{--or:#F57C00;--or2:#E65100;--bl:#E3F2FD;--bl2:#90CAF9;--bg:#FFFFFF;--tx:#1f2a37;--card:#FFFFFF;--bd:#BBDEFB}
@media (prefers-color-scheme:dark){:root{--bl:#14202c;--bl2:#2f5d86;--bg:#0f1720;--tx:#e8eef5;--card:#17212c;--bd:#2f5d86}}
*{box-sizing:border-box}
body{margin:0;background:var(--bl);color:var(--tx);font-family:"Segoe UI",Tahoma,Arial,sans-serif;min-height:100vh}
header{background:var(--or);color:#fff;text-align:center;padding:22px 12px;border-bottom:5px solid var(--bl2)}
header h1{margin:0;font-family:Georgia,"Times New Roman",serif;font-size:2.4rem;letter-spacing:2px}
header p{margin:6px 0 0;opacity:.95}
main{max-width:820px;margin:22px auto;padding:0 14px;display:grid;gap:18px}
.card{background:var(--card);border:2px solid var(--bd);border-top:5px solid var(--or);border-radius:10px;padding:16px;box-shadow:0 3px 10px rgba(0,0,0,.08)}
.card h2{margin:0 0 10px;font-family:Georgia,serif;font-size:1.15rem;color:var(--or2)}
textarea,.out,input[type=text],input[type=password]{width:100%;border:2px solid var(--bd);border-radius:8px;padding:12px;font:inherit;font-size:1.05rem;background:var(--bg);color:var(--tx)}
textarea,.out{min-height:120px;resize:vertical}
.out{direction:ltr;text-align:left;white-space:pre-wrap;font-family:Georgia,serif;font-size:1.25rem}
.out.rtl{direction:rtl;text-align:right;font-family:"Segoe UI",Tahoma,Arial,sans-serif}
.row{display:flex;flex-wrap:wrap;gap:8px;margin-top:10px;align-items:center}
button{font:inherit;cursor:pointer;border:0;border-radius:8px;padding:10px 16px;background:var(--or);color:#fff;font-weight:600}
button:hover{background:var(--or2)}
button.alt{background:var(--bl);color:var(--or2);border:2px solid var(--bl2)}
button.alt:hover{background:var(--bl2);color:#fff}
button.rec{background:#c62828}
button:disabled{opacity:.5;cursor:not-allowed}
.rep{display:flex;align-items:center;gap:6px;border:2px solid var(--bl2);border-radius:8px;padding:4px 8px;background:var(--bl)}
.rep button{padding:4px 12px;font-size:1.2rem}
.rep b{min-width:28px;text-align:center;font-size:1.1rem}
.syl{direction:ltr;display:flex;flex-wrap:wrap;gap:12px;min-height:60px}
.word{border:2px solid var(--bl2);background:var(--bl);border-radius:8px;padding:8px 12px;text-align:center;cursor:pointer}
.word .s{font-size:1.3rem;font-weight:700;color:var(--or2);font-family:Georgia,serif}
.word .a{font-size:.95rem;margin-top:2px;direction:rtl}
.hint{color:#6b7c8d;font-size:.9rem;margin-top:8px}
.sub{margin:14px 0 8px;font-weight:700;color:var(--or2)}
.items{display:grid;gap:8px}
.item{border:2px solid var(--bl2);background:var(--bl);border-radius:8px;padding:8px 12px;cursor:pointer}
.item .e{direction:ltr;text-align:left;font-family:Georgia,serif;font-size:1.1rem}
.item .r{direction:rtl;text-align:right;color:#6b7c8d;margin-top:2px}
#msg{text-align:center;min-height:22px;color:var(--or2);font-weight:600}
header{position:relative}
#gear{position:absolute;top:14px;left:14px;background:rgba(255,255,255,.2);font-size:1.3rem;padding:6px 12px}
#gear:hover{background:rgba(255,255,255,.35)}
#ov{display:none;position:fixed;inset:0;background:rgba(0,0,0,.4);z-index:20}
#ov.on{display:block}
#drawer{position:fixed;top:0;bottom:0;left:0;width:min(340px,88vw);background:var(--card);color:var(--tx);z-index:30;padding:16px;transform:translateX(-105%);transition:transform .25s;overflow:auto;border-right:4px solid var(--or);display:flex;flex-direction:column;gap:8px}
#drawer.on{transform:none}
#drawer .dh{display:flex;justify-content:space-between;align-items:center;color:var(--or2);font-size:1.1rem}
#drawer label{font-weight:700;margin-top:6px}
.kr{display:grid;gap:8px}
a{color:var(--or2)}
</style>
</head>
<body>
<header><button id="gear" title="الإعدادات" aria-label="الإعدادات">⚙️</button><h1>Teacher</h1><p>مترجمك ومعلمك للنطق الإنجليزي — بالذكاء الاصطناعي Gemini</p></header>
<div id="ov"></div>
<aside id="drawer" aria-hidden="true">
<div class="dh"><b>⚙️ الإعدادات</b><button id="dx" class="alt" aria-label="إغلاق">✕</button></div>
<label>مفتاح Gemini API</label>
<input type="password" id="key" placeholder="الصق المفتاح هنا" autocomplete="off" dir="ltr">
<label>النموذج</label>
<input type="text" id="model" dir="ltr" value="gemini-flash-latest">
<div class="row"><button id="saveKey">حفظ</button><button id="delKey" class="alt">حذف المفتاح</button></div>
<div class="hint" id="kst"></div>
<div class="hint">احصل على مفتاح مجاني من <a href="https://aistudio.google.com/apikey" target="_blank" rel="noopener">aistudio.google.com/apikey</a>. يُحفظ في متصفحك فقط ويُرسل إلى Google وحدها، وتدخله مرة واحدة.</div>
</aside>
<main>

<section class="card">
<h2>١ — النص (أي لغة)</h2>
<textarea id="ar" dir="auto" placeholder="اكتب نصاً بأي لغة، أو اضغط تحدث (بأي لغة بدون اختيار)، أو ارفع/اسحب ملفاً: صوت، صورة، PDF، Word، Excel، PowerPoint، نص..."></textarea>
<div class="row">
<button id="mic" class="alt">🎤 تحدث</button>
<button id="imgBtn" class="alt">📎 ارفع ملفات</button>
<input type="file" id="file" accept="audio/*,image/*,.pdf,.docx,.xlsx,.xls,.pptx,.csv,.tsv,.txt,.md,.html,.htm,.json,.xml,.srt,.vtt,.rtf,text/*" multiple hidden>
<button id="go">ترجمة ومعالجة ➜</button>
<button id="clr" class="alt">مسح</button>
</div>
<div class="hint">التعرف على الكلام يتم بواسطة Gemini ويميّز اللغة تلقائياً، دون اختيار لغة.</div>
</section>
<div id="msg"></div>

<section class="card">
<h2>٢ — المعنى (عربي ← إنجليزي، وإنجليزي ← عربي)</h2>
<div id="en" class="out" aria-live="polite"></div>
<div class="row">
<button id="nat">🔊 نطق طبيعي</button>
<button id="slow" class="alt">🐢 نطق بطيء</button>
<div class="rep" title="عدد مرات النطق"><span>التكرار</span><button class="alt" id="dn">−</button><b id="cnt">1</b><button class="alt" id="up">+</button></div>
</div>
</section>

<section class="card">
<h2>٣ — المقاطع الصوتية</h2>
<div id="syl" class="syl"></div>
<div class="hint">اضغط على أي كلمة لسماعها بنطق بطيء.</div>
</section>

<section class="card">
<h2>٤ — الاستخدام في جمل والمعاني المشابهة</h2>
<div class="sub">جمل توضح الاستخدام</div>
<div id="ex" class="items"></div>
<div class="sub">كلمات وجمل بمعنى مشابه</div>
<div id="sim" class="items"></div>
<div class="hint">اضغط على أي جملة لسماعها.</div>
</section>
</main>

<script>
(function(){
var $=function(i){return document.getElementById(i)};
var ar=$('ar'),en=$('en'),msg=$('msg'),sylBox=$('syl'),count=1,engText='';
var CDN='https://cdnjs.cloudflare.com/ajax/libs/',MAXC=6000,libP={};
function say(t){msg.textContent=t||''}
function esc(s){var d=document.createElement('div');d.textContent=s;return d.innerHTML}
window.addEventListener('error',function(e){say('خطأ: '+e.message)});

/* ---- Settings ---- */
function lsGet(k){try{return localStorage.getItem(k)||''}catch(_){return ''}}
function lsSet(k,v){try{localStorage.setItem(k,v)}catch(_){}}
$('key').value=lsGet('gkey');
$('model').value=lsGet('gmodel')||'gemini-flash-latest';
function drawer(on){$('drawer').classList.toggle('on',on);$('ov').classList.toggle('on',on);$('drawer').setAttribute('aria-hidden',on?'false':'true');if(on)$('key').focus()}
function kst(){$('kst').textContent=lsGet('gkey')?'✓ المفتاح محفوظ':'لم يُحفظ مفتاح بعد'}
$('gear').onclick=function(){drawer(true)};
$('dx').onclick=$('ov').onclick=function(){drawer(false)};
$('saveKey').onclick=function(){
 var k=$('key').value.trim();
 if(!k){say('الصق المفتاح أولاً');return}
 lsSet('gkey',k);lsSet('gmodel',$('model').value.trim()||'gemini-flash-latest');kst();say('تم الحفظ ✓ يمكنك الاستخدام الآن');drawer(false);
};
$('delKey').onclick=function(){lsSet('gkey','');$('key').value='';kst()};
kst();
if(!lsGet('gkey'))setTimeout(function(){drawer(true)},400);

/* ---- Gemini ---- */
async function gem(parts,json){
 var key=($('key').value||lsGet('gkey')).trim(),model=($('model').value||lsGet('gmodel')||'gemini-flash-latest').trim();
 if(!key){var e0=new Error('nokey');e0.nokey=1;throw e0}
 var body={contents:[{parts:parts}]};
 if(json)body.generationConfig={responseMimeType:'application/json'};
 var res=await fetch('https://generativelanguage.googleapis.com/v1beta/models/'+encodeURIComponent(model)+':generateContent',{method:'POST',headers:{'Content-Type':'application/json','x-goog-api-key':key},body:JSON.stringify(body)});
 var j={};try{j=await res.json()}catch(_){}
 if(!res.ok){var e=new Error((j.error&&j.error.message)||('HTTP '+res.status));e.status=res.status;throw e}
 var c=j.candidates&&j.candidates[0]&&j.candidates[0].content&&j.candidates[0].content.parts;
 return (c||[]).map(function(p){return p.text||''}).join('').trim();
}
function errMsg(e){
 if(e&&e.nokey){drawer(true);return 'أدخل مفتاح Gemini API في الإعدادات ثم اضغط حفظ'}
 if(e&&(e.status===400||e.status===403)&&/key|api/i.test(e.message))return 'مفتاح API غير صالح';
 if(e&&e.status===429)return 'تجاوزت الحد المسموح، انتظر قليلاً ثم حاول';
 if(e&&e.status===404)return 'اسم النموذج غير صحيح، غيّره في الإعداد';
 return 'تعذر الاتصال بـ Gemini: '+((e&&e.message)||'').slice(0,120);
}
function b64(blob){return new Promise(function(ok,no){var r=new FileReader();r.onload=function(){ok(String(r.result).split(',')[1])};r.onerror=no;r.readAsDataURL(blob)})}
function parse(t){var m=t.replace(/```json|```/g,'').trim();var a=m.indexOf('{'),b=m.lastIndexOf('}');return JSON.parse(m.slice(a,b+1))}

/* ---- Speech out (TTS) ---- */
function voice(){var v=speechSynthesis.getVoices();
 return v.find(function(x){return /en-US/i.test(x.lang)&&/natural|google|samantha|aria|jenny/i.test(x.name)})||v.find(function(x){return /^en/i.test(x.lang)})||null}
function speak(text,rate,times){
 if(!text||!window.speechSynthesis){say('المتصفح لا يدعم النطق');return}
 speechSynthesis.cancel();
 for(var i=0;i<times;i++){var u=new SpeechSynthesisUtterance(text);u.lang='en-US';u.rate=rate;var v=voice();if(v)u.voice=v;speechSynthesis.speak(u)}
}
$('nat').onclick=function(){speak(engText,0.95,count)};
$('slow').onclick=function(){speak(engText,0.55,count)};
$('up').onclick=function(){if(count<10)$('cnt').textContent=++count};
$('dn').onclick=function(){if(count>1)$('cnt').textContent=--count};

/* ---- Process text ---- */
var FORMAT='أعد JSON فقط بدون أي نص آخر بهذا الشكل: {"lang":"ar أو en أو other","original":"النص الأصلي كما هو","output":"إذا كان الأصل إنجليزياً فاكتب معناه بالعربية، وإلا فاكتب ترجمته الإنجليزية","english":"النص الإنجليزي المراد نطقه (هو الأصل إن كان إنجليزياً وإلا الترجمة)","words":[{"w":"word","s":"syl-la-ble","ar":"سيل-لا-بل"}],"examples":[{"en":"جملة إنجليزية قصيرة تستخدم النص","ar":"ترجمتها بالعربية"}],"similar":[{"en":"كلمة أو جملة إنجليزية بمعنى مشابه","ar":"معناها بالعربية"}]}. words تشمل كل كلمة في english بالترتيب (s المقاطع بشرطة، ar نطق المقاطع بحروف عربية بشرطة). examples ثلاث جمل، similar من ثلاثة إلى خمسة عناصر.';
function fill(id,items){
 var box=$(id);box.innerHTML='';
 (items||[]).forEach(function(x){
  var d=document.createElement('div');d.className='item';
  d.innerHTML='<div class="e">'+esc(x.en||'')+'</div><div class="r">'+esc(x.ar||'')+'</div>';
  d.onclick=function(){speak(x.en,0.9,1)};
  box.appendChild(d);
 });
}
function render(r){
 engText=r.english||'';
 en.textContent=r.output||r.english||'';
 en.className='out'+(r.lang==='en'?' rtl':'');
 fill('ex',r.examples);fill('sim',r.similar);
 sylBox.innerHTML='';
 (r.words||[]).forEach(function(x){
  var d=document.createElement('div');d.className='word';
  d.innerHTML='<div class="s">'+esc((x.s||x.w||'').replace(/-/g,' · '))+'</div><div class="a">'+esc((x.ar||'').replace(/-/g,' · '))+'</div>';
  d.onclick=function(){speak(x.w,0.5,1)};
  sylBox.appendChild(d);
 });
}
$('go').onclick=async function(){
 var t=ar.value.trim();if(!t){say('اكتب نصاً أولاً');return}
 $('go').disabled=true;say('جاري الترجمة...');
 try{
  var txt=await gem([{text:'حدد لغة النص التالي (عربي أو إنجليزي أو أي لغة أخرى) ثم عالجه. '+FORMAT+'\n\nالنص:\n'+t}],true);
  render(parse(txt));say('');
 }catch(e){say(errMsg(e))}
 $('go').disabled=false;
};
$('clr').onclick=function(){ar.value='';en.textContent='';engText='';sylBox.innerHTML='';$('ex').innerHTML='';$('sim').innerHTML='';say('')};

/* ---- Audio → text (Gemini) ---- */
async function toWav(blob){
 var ctx=new (window.AudioContext||window.webkitAudioContext)();
 var buf=await ctx.decodeAudioData(await blob.arrayBuffer());
 if(ctx.close)ctx.close();
 var sr=16000,off=new OfflineAudioContext(1,Math.max(1,Math.ceil(buf.duration*sr)),sr);
 var src=off.createBufferSource();src.buffer=buf;src.connect(off.destination);src.start();
 var d=(await off.startRendering()).getChannelData(0),o=new DataView(new ArrayBuffer(44+d.length*2));
 function w(p,s){for(var i=0;i<s.length;i++)o.setUint8(p+i,s.charCodeAt(i))}
 w(0,'RIFF');o.setUint32(4,36+d.length*2,true);w(8,'WAVE');w(12,'fmt ');o.setUint32(16,16,true);o.setUint16(20,1,true);o.setUint16(22,1,true);o.setUint32(24,sr,true);o.setUint32(28,sr*2,true);o.setUint16(32,2,true);o.setUint16(34,16,true);w(36,'data');o.setUint32(40,d.length*2,true);
 for(var i=0;i<d.length;i++){var v=Math.max(-1,Math.min(1,d[i]));o.setInt16(44+i*2,v<0?v*32768:v*32767,true)}
 return new Blob([o],{type:'audio/wav'});
}
async function transcribe(blob){
 var send=blob;
 try{send=await toWav(blob)}catch(_){}
 if(send.size>14*1024*1024)throw new Error('الملف الصوتي كبير، استخدم ملفاً أقصر (حتى نحو ٧ دقائق)');
 return gem([{inlineData:{mimeType:send.type||blob.type||'audio/wav',data:await b64(send)}},{text:'اكتب بدقة كل الكلام في هذا التسجيل بلغته الأصلية (أياً كانت اللغة) وبحروفها الأصلية، بدون ترجمة وبدون أي شرح أو تعليق. إذا لم يوجد كلام فاكتب فقط: [لا يوجد كلام]'}]).then(function(t){return t==='[لا يوجد كلام]'?'':t});
}

/* ---- Microphone ---- */
var mr=null,chunks=[],stream=null,recording=false;
function setMic(on){recording=on;$('mic').textContent=on?'⏹ إيقاف':'🎤 تحدث';$('mic').className=on?'rec':'alt'}
$('mic').onclick=async function(){
 if(recording){if(mr&&mr.state!=='inactive')mr.stop();return}
 if(!lsGet('gkey')&&!$('key').value.trim()){drawer(true);say('أدخل مفتاح Gemini أولاً');return}
 if(!navigator.mediaDevices||!window.MediaRecorder){say('المتصفح أو طريقة الفتح لا تدعم التسجيل. افتح الملف في Chrome أو Edge (وعلى iPhone: Safari 14.5 أو أحدث)');return}
 try{stream=await navigator.mediaDevices.getUserMedia({audio:true})}
 catch(e){var n=e&&e.name;say(n==='NotAllowedError'?'الميكروفون ممنوع: اسمح له من أيقونة القفل بجوار عنوان الصفحة. وإن فتحت الملف داخل Claude فافتحه مباشرة في المتصفح':n==='NotFoundError'?'لا يوجد ميكروفون في هذا الجهاز':n==='NotReadableError'?'الميكروفون مستخدم من برنامج آخر':'تعذر تشغيل الميكروفون ('+(n||'؟')+')');return}
 chunks=[];mr=new MediaRecorder(stream);
 mr.ondataavailable=function(e){if(e.data&&e.data.size)chunks.push(e.data)};
 mr.onstop=async function(){
  stream.getTracks().forEach(function(t){t.stop()});setMic(false);
  var blob=new Blob(chunks,{type:mr.mimeType||'audio/webm'});
  if(!blob.size){say('لم يتم تسجيل صوت');return}
  $('go').disabled=true;$('mic').disabled=true;say('جاري تحويل الصوت إلى نص...');
  try{
   var t=await transcribe(blob);
   if(!t){say('لم أسمع كلاماً، حاول مرة أخرى')}
   else{ar.value=(ar.value+' '+t).trim();$('go').disabled=false;$('mic').disabled=false;$('go').onclick();return}
  }catch(e){say(errMsg(e))}
  $('go').disabled=false;$('mic').disabled=false;
 };
 mr.start();setMic(true);say('🎤 جاري الاستماع... تحدث بأي لغة ثم اضغط إيقاف');
};

/* ---- Files ---- */
function loadLib(src){return libP[src]||(libP[src]=new Promise(function(ok,no){var t=document.createElement('script');t.src=src;t.onload=ok;t.onerror=function(){delete libP[src];no(new Error('lib'))};document.head.appendChild(t)}))}
function ext(f){var m=/\.([^.]+)$/.exec(f.name||'');return m?m[1].toLowerCase():''}
function isAudio(f){return (f.type||'').indexOf('audio/')===0||/^(mp3|wav|m4a|ogg|oga|aac|flac|opus|weba|webm)$/.test(ext(f))&&(f.type||'').indexOf('video/')!==0&&ext(f)!=='webm'||(ext(f)==='webm'&&(f.type||'').indexOf('audio/')===0)}
async function viaGemini(f,prompt,mime){
 if(f.size>14*1024*1024)throw new Error('الملف كبير (الحد نحو ١٤ ميغابايت)');
 var t=await gem([{inlineData:{mimeType:mime,data:await b64(f)}},{text:prompt}]);
 return t==='[لا يوجد نص]'?'':t;
}
var OCR='اقرأ كل النص الموجود في هذا الملف (أياً كانت لغته) واكتبه كما هو بالترتيب بدون أي شرح أو تعليق. إذا لم يوجد نص فاكتب فقط: [لا يوجد نص]';
async function readOffice(f,e){
 if(e==='docx'){await loadLib('https://cdn.jsdelivr.net/npm/mammoth@1.6.0/mammoth.browser.min.js');return (await mammoth.extractRawText({arrayBuffer:await f.arrayBuffer()})).value}
 if(e==='xlsx'||e==='xls'){await loadLib(CDN+'xlsx/0.18.5/xlsx.full.min.js');var wb=XLSX.read(await f.arrayBuffer(),{type:'array'});return wb.SheetNames.map(function(n){return n+':\n'+XLSX.utils.sheet_to_csv(wb.Sheets[n])}).join('\n\n')}
 if(e==='pptx'){
  await loadLib(CDN+'jszip/3.10.1/jszip.min.js');
  var z=await JSZip.loadAsync(await f.arrayBuffer()),names=Object.keys(z.files).filter(function(n){return /^ppt\/slides\/slide\d+\.xml$/.test(n)}).sort(function(a,b){return parseInt(a.replace(/\D/g,''))-parseInt(b.replace(/\D/g,''))}),out=[];
  for(var i=0;i<names.length;i++){var x=await z.files[names[i]].async('string');out.push((x.match(/<a:t>[^<]*<\/a:t>/g)||[]).map(function(t){return t.replace(/<[^>]+>/g,'')}).join(' '))}
  return out.join('\n\n');
 }
 throw new Error('unsupported');
}
async function readAny(f){
 var e=ext(f),ty=f.type||'';
 if(isAudio(f))return transcribe(f);
 if(ty.indexOf('image/')===0)return viaGemini(f,OCR,ty);
 if(e==='pdf'||ty==='application/pdf')return viaGemini(f,OCR,'application/pdf');
 if(e==='docx'||e==='xlsx'||e==='xls'||e==='pptx')return readOffice(f,e);
 if(e==='doc'||e==='ppt')throw new Error('unsupported');
 var t=await f.text();
 if(t.indexOf('\u0000')>-1||(t.match(/\uFFFD/g)||[]).length>20)throw new Error('unsupported');
 if(e==='html'||e==='htm')t=new DOMParser().parseFromString(t,'text/html').body.textContent;
 if(e==='rtf')t=t.replace(/\\[a-z]+-?\d* ?|[{}]/g,'');
 return t;
}
async function handleFiles(all){
 ar.value='';$('go').disabled=true;$('imgBtn').disabled=true;$('mic').disabled=true;
 var texts=[],failed=0,unsup=0,lastErr=null;
 for(var i=0;i<all.length;i++){
  say('جاري قراءة الملف '+(i+1)+' من '+all.length+': '+all[i].name);
  try{
   var t=((await readAny(all[i]))||'').trim();
   if(t){texts.push(all.length>1?'['+all[i].name+']\n'+t:t);ar.value=texts.join('\n\n')}
  }catch(err){
   if(err&&err.message==='unsupported')unsup++;else{failed++;lastErr=err}
   if(err&&err.nokey)break;
  }
 }
 $('go').disabled=false;$('imgBtn').disabled=false;$('mic').disabled=false;
 if(!texts.length){say(lastErr?errMsg(lastErr):unsup?'نوع الملف غير مدعوم (جرّب صوت أو صورة أو pdf أو docx أو xlsx أو pptx أو txt)':'لم يتم العثور على نص في الملفات');return}
 if(ar.value.length>MAXC){ar.value=ar.value.slice(0,MAXC);say('تم أخذ أول '+MAXC+' حرف فقط من النص')}
 else say(failed||unsup?'تعذرت قراءة '+(failed+unsup)+' ملف، سيتم معالجة الباقي...':'');
 $('go').onclick();
}
$('imgBtn').onclick=function(){$('file').click()};
$('file').onchange=function(e){var a=Array.from(e.target.files);e.target.value='';if(a.length)handleFiles(a)};
['dragover','drop'].forEach(function(n){document.addEventListener(n,function(e){e.preventDefault();if(n==='drop'&&e.dataTransfer&&e.dataTransfer.files.length)handleFiles(Array.from(e.dataTransfer.files))})});
ar.addEventListener('paste',function(e){var fs=Array.from((e.clipboardData&&e.clipboardData.files)||[]);if(fs.length){e.preventDefault();handleFiles(fs)}});
})();
</script>
</body>
</html>
