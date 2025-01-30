# GUILLAUME
LOVE ROOM
import { useState } from "react";
import { Button } from "@/components/ui/button";
import { Input } from "@/components/ui/input";
import { Textarea } from "@/components/ui/textarea";
import { Card, CardContent } from "@/components/ui/card";
import { Mail, Phone, MapPin, Calendar } from "lucide-react";
import { motion } from "framer-motion";

function CalendarComponent() {
  return <div className="text-center text-gray-500">Planning des disponibilités en cours d'ajout...</div>;
}

export default function Home() {
  const [formData, setFormData] = useState({ name: "", email: "", message: "" });

  const handleChange = (e) => {
    setFormData({ ...formData, [e.target.name]: e.target.value });
  };

  const handleSubmit = (e) => {
    e.preventDefault();
    alert("Votre demande a été envoyée !");
  };

  return (
    <div className="min-h-screen bg-[#D2B48C] text-[#5C4033]">
      <header className="bg-[#8B5A2B] text-white p-6 text-center text-xl font-bold">
        L'Abri des Douceurs - Location avec Spa
      </header>

      <main className="container mx-auto p-6">
        <motion.div initial={{ opacity: 0 }} animate={{ opacity: 1 }} transition={{ duration: 1 }}>
          <h2 className="text-2xl font-bold text-center mb-6">Un lieu unique et romantique</h2>
          <p className="text-center text-[#6F4E37] max-w-2xl mx-auto">
            Niché au cœur de Bourgoin-Jallieu, entre la gare et la rue piétonne, notre cave voûtée en pierre vous invite à un séjour hors du temps. 
            Profitez d’un cadre intimiste et reposant, agrémenté d’un spa privatif, pour une escapade romantique inoubliable. 
            Avec de nombreux restaurants à proximité, c’est l’endroit idéal pour une soirée en amoureux.
          </p>
        </motion.div>

        <div className="grid md:grid-cols-2 gap-6 my-8">
          <img src="/spa.jpg" alt="Spa privé" className="rounded-xl shadow-md" />
          <img src="/cave.jpg" alt="Cave voûtée" className="rounded-xl shadow-md" />
        </div>

        <Card className="p-6 my-8">
          <CardContent>
            <h3 className="text-xl font-bold mb-4">Réserver votre séjour</h3>
            <form onSubmit={handleSubmit} className="grid gap-4">
              <Input name="name" placeholder="Votre nom" onChange={handleChange} required />
              <Input type="email" name="email" placeholder="Votre email" onChange={handleChange} required />
              <Textarea name="message" placeholder="Votre message" onChange={handleChange} required />
              <Button type="submit" className="bg-[#8B5A2B] text-white">Envoyer</Button>
            </form>
          </CardContent>
        </Card>

        <Card className="p-6 my-8">
          <CardContent>
            <h3 className="text-xl font-bold mb-4 flex items-center"><Calendar className="w-5 h-5 mr-2" /> Disponibilités</h3>
            <CalendarComponent />
          </CardContent>
        </Card>
      </main>

      <footer className="bg-[#8B5A2B] text-white p-6 text-center mt-8">
        <div className="flex justify-center space-x-4">
          <span className="flex items-center"><Mail className="w-5 h-5 mr-2" /> contact@labridesdouceurs.fr</span>
          <span className="flex items-center"><Phone className="w-5 h-5 mr-2" /> 06 71 53 91 02</span>
          <span className="flex items-center"><MapPin className="w-5 h-5 mr-2" /> Bourgoin-Jallieu</span>
        </div>
      </footer>
    </div>
  );
}
