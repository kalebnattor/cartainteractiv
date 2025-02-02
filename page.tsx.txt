"use client"

import { useState } from "react"
import { motion } from "framer-motion"

export default function Home() {
  const [isFlipped, setIsFlipped] = useState(false)
  const [isOpen, setIsOpen] = useState(false)

  const handleEnvelopeClick = () => {
    if (isFlipped) {
      setIsOpen(!isOpen)
    } else {
      setIsFlipped(true)
    }
  }

  return (
    <main className="flex min-h-screen items-center justify-center bg-gray-100">
      <motion.div
        className="relative w-80 h-60 cursor-pointer"
        animate={{ rotateY: isFlipped ? 180 : 0 }}
        transition={{ duration: 0.6 }}
        onClick={handleEnvelopeClick}
        style={{ transformStyle: "preserve-3d" }}
      >
        {/* Front of the envelope */}
        <div className="absolute w-full h-full backface-hidden">
          <svg viewBox="0 0 100 75" className="w-full h-full fill-yellow-200 stroke-yellow-600">
            <path d="M0,0 L100,0 L100,75 L0,75 Z" />
            <path d="M0,0 L50,40 L100,0" className="stroke-2" />
            <path d="M0,75 L50,35 L100,75" className="stroke-2" />
          </svg>
          <div className="absolute top-1/2 left-1/2 transform -translate-x-1/2 -translate-y-1/2 text-center">
            <p className="text-sm font-semibold text-gray-700">To: Mey</p>
            <p className="text-sm font-semibold text-gray-700">From: Kalebcito</p>
          </div>
        </div>

        {/* Back of the envelope */}
        <div className="absolute w-full h-full backface-hidden" style={{ transform: "rotateY(180deg)" }}>
          <svg viewBox="0 0 100 75" className="w-full h-full fill-yellow-200 stroke-yellow-600">
            <path d="M0,0 L100,0 L100,75 L0,75 Z" />
          </svg>

          {/* Letter */}
          <motion.div
            className="absolute top-1/2 left-1/2 w-3/4 h-3/4 bg-white shadow-md"
            style={{ originY: 0.5, originX: 0.5 }}
            initial={{ scale: 0.5, y: "25%" }}
            animate={isOpen ? { scale: 1, y: "-60%" } : { scale: 0.5, y: "25%" }}
          >
            <div className="p-4 text-sm">
              <h2 className="font-bold mb-2">Para mi princesa,</h2>
              <p>Hace practicamente un año te estaba pidiendo ser mi san valentina, quería que fuera algo especial y
        bonito para los dos, algo que se volvió realidad con el día tan hermoso que tuvimos. Este año no va a ser
        excepción entonces espero te guste este detallito que te preparé en este link:</p>
              <p className="mt-4">Con amor,</p>
              <p>Kalebcito</p>
            </div>
          </motion.div>
        </div>
      </motion.div>
    </main>
  )
}