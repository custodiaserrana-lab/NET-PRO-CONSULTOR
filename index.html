import { useState, useRef, useEffect } from "react";

const SYSTEM_PROMPT = `Sos un especialista en redes de comunicaciones con más de 50 años de experiencia profesional. Tenés posgrado y magistrado en telecomunicaciones. Sos experto en redes hogareñas y empresariales, especialmente en:
- Módems Huawei (HG8245, EG8145, B618, HG532, y todos los modelos hogareños)
- Optimización para streaming, IPTV, fútbol en vivo, señales codificadas (DirecTV, TyC Sports, ESPN, etc.)
- Configuración de QoS, DNS, canales WiFi, separación de redes, VLANs básicas
- Diagnóstico de latencia, buffering, cortes de señal, tildes y cuelgues
- Armado de redes hogareñas de alta performance con bajo presupuesto

Respondés de forma directa, técnica pero comprensible. Das consejos concretos y pasos accionables. Usás términos técnicos pero siempre los explicás brevemente. Respondés en español rioplatense. Sos confiado y claro. Máximo 4 párrafos por respuesta. Nunca decís "no puedo ayudarte" — siempre das una solución o un camino concreto.`;

const QUICK = [
  "¿Por qué se tilda mi Huawei?",
  "Ver fútbol sin cortes",
  "Mejorar WiFi para streaming",
  "Configurar DNS rápido",
  "¿Necesito otro router?",
  "Cable directo vs WiFi",
];

const CONFIG_ROWS = [
  { key: "DNS Primario", val: "1.1.1.1", note: "Cloudflare — el más rápido" },
  { key: "DNS Secundario", val: "8.8.8.8", note: "Google DNS — respaldo" },
  { key: "Banda 5GHz — Canal", val: "36 / 40 / 44", note: "UNII-1, menor interferencia" },
  { key: "Banda 2.4GHz — Canal", val: "1, 6 o 11", note: "Únicos canales sin overlap" },
  { key: "MTU", val: "1500", note: "Óptimo para streaming" },
  { key: "QoS", val: "HABILITADO", note: "Prioridad a TV / streaming" },
  { key: "Reinicio programado", val: "3:00 AM", note: "Limpia RAM y tablas ARP" },
];

const STEPS = [
  { n:"01", title:"Medí la velocidad real", desc:"Entrá a fast.com conectado por cable directo al modem. Ese número es tu techo real. Si hay diferencia grande con lo contratado, hay problema en la línea.", badge:"CRÍTICO", color:"#ff3b3b" },
  { n:"02", title:"Accedé al panel Huawei (192.168.100.1)", desc:'Usuario: admin / admin (o el del sticker). Desde ahí controlás todo. Si nunca entraste, es hora de conocer tu red.', badge:"PASO BASE", color:"#e8ff00" },
  { n:"03", title:"Cambiá los DNS a 1.1.1.1 / 8.8.8.8", desc:"Los DNS del proveedor suelen tardar 200-400ms. Con Cloudflare bajás eso a 10-20ms. Cambio gratuito, impacto inmediato.", badge:"ALTO IMPACTO", color:"#e8ff00" },
  { n:"04", title:"Creá una red 5GHz solo para streaming", desc:'En el panel Huawei, creá una SSID secundaria en 5GHz. Llamala "Streaming-5G" y conectá solo tu Smart TV o decodificador.', badge:"ALTO IMPACTO", color:"#e8ff00" },
  { n:"05", title:"Habilitá QoS con prioridad al TV", desc:"En Configuración Avanzada › QoS, asigná máxima prioridad a la MAC de tu televisor. Cuando compite el ancho de banda, tu partido siempre gana.", badge:"ESENCIAL", color:"#00ffa3" },
  { n:"06", title:"Cable UTP Cat6 directo al Smart TV", desc:"La WiFi más potente no supera un buen cable. 10 metros de Cat6 eliminan el 90% de los cortes para señales codificadas.", badge:"RECOMENDADO", color:"#00ffa3" },
];

export default function App() {
  const [messages, setMessages] = useState([
    { role: "assistant", text: "Buenas. Soy tu especialista en redes con más de 50 años en el campo. Contame qué problema tenés: lentitud, cortes, buffering, señal débil... y te doy el diagnóstico y la solución concreta. No hay problema de red sin solución técnica." }
  ]);
  const [input, setInput] = useState("");
  const [loading, setLoading] = useState(false);
  const [activeTab, setActiveTab] = useState("chat");
  const bottomRef = useRef(null);

  useEffect(() => {
    bottomRef.current?.scrollIntoView({ behavior: "smooth" });
  }, [messages, loading]);

  async function send() {
    const text = input.trim();
    if (!text || loading) return;
    const newMsgs = [...messages, { role: "user", text }];
    setMessages(newMsgs);
    setInput("");
    setLoading(true);
    try {
      const apiMessages = newMsgs.map(m => ({ role: m.role === "assistant" ? "assistant" : "user", content: m.text }));
      const res = await fetch("https://api.anthropic.com/v1/messages", {
        method: "POST",
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify({ model: "claude-sonnet-4-20250514", max_tokens: 1000, system: SYSTEM_PROMPT, messages: apiMessages })
      });
      const data = await res.json();
      const reply = data.content?.find(b => b.type === "text")?.text || "Error al procesar. Intentá de nuevo.";
      setMessages(prev => [...prev, { role: "assistant", text: reply }]);
    } catch {
      setMessages(prev => [...prev, { role: "assistant", text: "Error de conexión. Revisá tu red e intentá de nuevo." }]);
    }
    setLoading(false);
  }

  return (
    <div style={{ background: "#0a0a0a", minHeight: "100vh", color: "#d0d0d0", fontFamily: "'Segoe UI', system-ui, sans-serif", position: "relative" }}>
      {/* BG */}
      <div style={{ position: "fixed", inset: 0, backgroundImage: "linear-gradient(rgba(255,255,255,0.012) 1px, transparent 1px), linear-gradient(90deg, rgba(255,255,255,0.012) 1px, transparent 1px)", backgroundSize: "60px 60px", pointerEvents: "none" }} />
      <div style={{ position: "fixed", inset: 0, background: "radial-gradient(ellipse 70% 50% at 15% 20%, rgba(232,255,0,0.04) 0%, transparent 60%)", pointerEvents: "none" }} />

      <div style={{ position: "relative", maxWidth: 960, margin: "0 auto", padding: "0 20px" }}>

        {/* HEADER */}
        <header style={{ borderBottom: "1px solid #2a2a2a", padding: "28px 0 24px" }}>
          <div style={{ display: "flex", justifyContent: "space-between", alignItems: "flex-end", flexWrap: "wrap", gap: 16 }}>
            <div>
              <div style={{ fontFamily: "monospace", fontSize: 11, color: "#e8ff00", letterSpacing: 4, textTransform: "uppercase", marginBottom: 4 }}>// especialista certificado en redes</div>
              <div style={{ fontSize: "clamp(40px,8vw,64px)", fontWeight: 900, lineHeight: 1, color: "#f0f0f0", letterSpacing: 2 }}>
                NET<span style={{ color: "#e8ff00" }}>PRO</span>
              </div>
              <div style={{ fontSize: 13, color: "#aaa", marginTop: 4 }}>Consultoría Avanzada · Redes Hogareñas & Empresariales</div>
            </div>
            <div style={{ display: "flex", flexDirection: "column", gap: 6, alignItems: "flex-end" }}>
              {["50+ años de experiencia", "Posgrado + Magistrado Telecomunicaciones", "Experto Huawei / Streaming / IPTV"].map(c => (
                <div key={c} style={{ display: "flex", alignItems: "center", gap: 8, padding: "5px 12px", border: "1px solid #2a2a2a", background: "#1a1a1a", borderRadius: 2, fontFamily: "monospace", fontSize: 11, color: "#aaa", whiteSpace: "nowrap" }}>
                  <span style={{ width: 6, height: 6, borderRadius: "50%", background: "#00ffa3", display: "inline-block", animation: "none" }} />
                  {c}
                </div>
              ))}
            </div>
          </div>
        </header>

        {/* MÉTRICAS */}
        <div style={{ display: "grid", gridTemplateColumns: "repeat(4, 1fr)", gap: 1, background: "#2a2a2a", border: "1px solid #2a2a2a", margin: "28px 0" }}>
          {[["80%","fallas resueltas con config"],["4K","streaming estable 25 Mbps"],["<20ms","latencia con QoS activo"],["Wi-Fi 6","estándar recomendado"]].map(([n,l]) => (
            <div key={n} style={{ background: "#141414", padding: "20px 16px" }}>
              <div style={{ fontSize: 36, fontWeight: 900, color: "#e8ff00", lineHeight: 1 }}>{n}</div>
              <div style={{ fontFamily: "monospace", fontSize: 11, color: "#666", marginTop: 4, lineHeight: 1.4 }}>{l}</div>
            </div>
          ))}
        </div>

        {/* TABS */}
        <div style={{ display: "flex", gap: 0, borderBottom: "1px solid #2a2a2a", marginBottom: 0 }}>
          {[["chat","💬 Consultá al Especialista"],["config","⚙️ Config Huawei"],["pasos","📋 Protocolo de Optimización"]].map(([id, label]) => (
            <button key={id} onClick={() => setActiveTab(id)} style={{ padding: "12px 20px", background: activeTab === id ? "#1a1a1a" : "transparent", border: "none", borderBottom: activeTab === id ? "2px solid #e8ff00" : "2px solid transparent", color: activeTab === id ? "#e8ff00" : "#666", cursor: "pointer", fontFamily: "monospace", fontSize: 12, letterSpacing: 1, transition: "all 0.2s" }}>
              {label}
            </button>
          ))}
        </div>

        {/* TAB: CHAT */}
        {activeTab === "chat" && (
          <div style={{ border: "1px solid #2a2a2a", borderTop: "none", background: "#0d0d0d", marginBottom: 40 }}>
            {/* Quick chips */}
            <div style={{ display: "flex", gap: 8, flexWrap: "wrap", padding: "12px 16px", borderBottom: "1px solid #1e1e1e" }}>
              {QUICK.map(q => (
                <button key={q} onClick={() => setInput(q)} style={{ padding: "5px 12px", border: "1px solid #2a2a2a", background: "#141414", color: "#aaa", fontSize: 12, fontFamily: "monospace", cursor: "pointer", borderRadius: 2, transition: "all 0.2s" }}
                  onMouseEnter={e => { e.target.style.borderColor = "#00ffa3"; e.target.style.color = "#00ffa3"; }}
                  onMouseLeave={e => { e.target.style.borderColor = "#2a2a2a"; e.target.style.color = "#aaa"; }}>
                  {q}
                </button>
              ))}
            </div>

            {/* Messages */}
            <div style={{ padding: 16, display: "flex", flexDirection: "column", gap: 12, maxHeight: 420, overflowY: "auto" }}>
              {messages.map((m, i) => (
                <div key={i} style={{ maxWidth: "82%", alignSelf: m.role === "user" ? "flex-end" : "flex-start", padding: "12px 16px", background: m.role === "user" ? "rgba(0,255,163,0.07)" : "#1a1a1a", border: m.role === "user" ? "1px solid rgba(0,255,163,0.2)" : "1px solid #2a2a2a", borderLeft: m.role === "assistant" ? "3px solid #e8ff00" : undefined, fontSize: 14, lineHeight: 1.65, color: m.role === "user" ? "#f0f0f0" : "#d0d0d0", textAlign: m.role === "user" ? "right" : "left", whiteSpace: "pre-wrap" }}>
                  {m.text}
                </div>
              ))}
              {loading && (
                <div style={{ display: "flex", gap: 5, padding: "12px 16px", background: "#1a1a1a", border: "1px solid #2a2a2a", borderLeft: "3px solid #e8ff00", width: "fit-content", alignItems: "center" }}>
                  {[0,0.2,0.4].map((d,i) => (
                    <div key={i} style={{ width: 7, height: 7, borderRadius: "50%", background: "#e8ff00", animation: `bounce 1.2s ${d}s infinite` }} />
                  ))}
                </div>
              )}
              <div ref={bottomRef} />
            </div>

            {/* Input */}
            <div style={{ display: "flex", gap: 8, padding: "12px 16px", borderTop: "1px solid #1e1e1e" }}>
              <input
                value={input}
                onChange={e => setInput(e.target.value)}
                onKeyDown={e => e.key === "Enter" && send()}
                placeholder="Describí tu problema de red..."
                disabled={loading}
                style={{ flex: 1, background: "#141414", border: "1px solid #2a2a2a", color: "#d0d0d0", padding: "10px 14px", fontFamily: "inherit", fontSize: 14, outline: "none", borderRadius: 2 }}
              />
              <button onClick={send} disabled={loading || !input.trim()} style={{ background: loading ? "#333" : "#e8ff00", color: "#0a0a0a", border: "none", padding: "10px 24px", fontWeight: 900, fontSize: 14, letterSpacing: 1, cursor: loading ? "not-allowed" : "pointer", borderRadius: 2, transition: "all 0.2s" }}>
                {loading ? "..." : "ENVIAR"}
              </button>
            </div>
          </div>
        )}

        {/* TAB: CONFIG HUAWEI */}
        {activeTab === "config" && (
          <div style={{ border: "1px solid #2a2a2a", borderTop: "none", background: "#141414", marginBottom: 40 }}>
            <div style={{ padding: "14px 20px", borderBottom: "1px solid #2a2a2a", background: "#1a1a1a", display: "flex", justifyContent: "space-between" }}>
              <span style={{ fontFamily: "monospace", fontSize: 12, color: "#00ffa3" }}>// MODEM HUAWEI — HG8245 / EG8145 / B618 / HG532</span>
              <span style={{ width: 8, height: 8, borderRadius: "50%", background: "#00ffa3", display: "inline-block" }} />
            </div>
            {CONFIG_ROWS.map(r => (
              <div key={r.key} style={{ display: "grid", gridTemplateColumns: "1fr 1fr 1.5fr", gap: 16, padding: "14px 20px", borderBottom: "1px solid #1e1e1e", alignItems: "center" }}>
                <span style={{ fontFamily: "monospace", fontSize: 13, color: "#aaa" }}>{r.key}</span>
                <span style={{ fontFamily: "monospace", fontSize: 13, color: "#e8ff00", fontWeight: 700 }}>{r.val}</span>
                <span style={{ fontSize: 12, color: "#666", textAlign: "right" }}>{r.note}</span>
              </div>
            ))}
            <div style={{ padding: "16px 20px", background: "rgba(232,255,0,0.03)", borderTop: "1px solid rgba(232,255,0,0.15)" }}>
              <span style={{ fontFamily: "monospace", fontSize: 11, color: "#e8ff00" }}>// Acceso al panel: http://192.168.100.1 — usuario: admin / contraseña: admin (o ver sticker del modem)</span>
            </div>
          </div>
        )}

        {/* TAB: PASOS */}
        {activeTab === "pasos" && (
          <div style={{ borderTop: "none", marginBottom: 40, display: "flex", flexDirection: "column", gap: 8, paddingTop: 16 }}>
            {STEPS.map(s => (
              <div key={s.n} style={{ display: "grid", gridTemplateColumns: "48px 1fr auto", gap: 16, padding: "18px 20px", border: "1px solid #2a2a2a", background: "#141414", alignItems: "start", transition: "all 0.2s", cursor: "default" }}
                onMouseEnter={e => { e.currentTarget.style.borderColor = s.color; e.currentTarget.style.transform = "translateX(4px)"; }}
                onMouseLeave={e => { e.currentTarget.style.borderColor = "#2a2a2a"; e.currentTarget.style.transform = "translateX(0)"; }}>
                <div style={{ fontWeight: 900, fontSize: 28, color: "#2a2a2a", lineHeight: 1, transition: "color 0.2s" }}>{s.n}</div>
                <div>
                  <div style={{ fontWeight: 700, fontSize: 15, color: "#f0f0f0", marginBottom: 6 }}>{s.title}</div>
                  <div style={{ fontSize: 13, color: "#aaa", lineHeight: 1.6 }}>{s.desc}</div>
                </div>
                <div style={{ padding: "4px 10px", border: `1px solid ${s.color}`, color: s.color, fontFamily: "monospace", fontSize: 10, whiteSpace: "nowrap", alignSelf: "flex-start" }}>{s.badge}</div>
              </div>
            ))}
          </div>
        )}

        {/* FOOTER */}
        <footer style={{ borderTop: "1px solid #1e1e1e", padding: "24px 0", display: "flex", justifyContent: "space-between", flexWrap: "wrap", gap: 12 }}>
          <div style={{ fontWeight: 900, fontSize: 20, color: "#444", letterSpacing: 2 }}>NET<span style={{ color: "#e8ff00" }}>PRO</span></div>
          <div style={{ fontFamily: "monospace", fontSize: 11, color: "#444", textAlign: "right", lineHeight: 1.8 }}>50+ años · Posgrado + Magistrado · Huawei · IPTV · Streaming</div>
        </footer>
      </div>

      <style>{`
        @keyframes bounce {
          0%,60%,100% { opacity:0.3; transform:translateY(0); }
          30% { opacity:1; transform:translateY(-4px); }
        }
      `}</style>
    </div>
  );
}
